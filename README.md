# Jamf Pro Docker Container - for dev testing

Create ephemeral dev environment for testing. **This uses the MySQL root user as this is dev only.**

> Jamf Pro does not support the latest MySQL version 8.x default authentication method. We need to change the default to mysql_native_password or Legacy Password Encryption method using my.cnf bind mount.
>Or alternatively, alter the user after database creation:
>```
>alter user 'jamfsoftware'@'localhost' identified with mysql_native_password by 'jamfsw03';
>```

1. Use the latest Jamf Pro Tomcat image tag as base image. 

	https://github.com/jamf/jamfpro

	```
	docker pull jamfdevops/jamfpro:0.0.13
	```

2. Download the current Jamf Pro ROOT.war collection to the same directory as the Dockerfile.

	https://www.jamf.com/jamf-nation/my/products

3. Build new docker image and append version tag.
	
	```
	docker build . -t jamfpro:10.42.1 -f ./Dockerfile
	```

4. Start containers on their own bridged network. 

	```
	docker compose up --detach
	```

5. Open browser - http://[container-ip]:8443
