# Jamf Pro Docker Container - for dev testing

Use the latest Jamf Pro Tomcat image tag as base image.

https://github.com/jamf/jamfpro
```
docker pull jamfdevops/jamfpro:0.0.13
```
Download the current Jamf Pro ROOT.war collection to the same directory as the Dockerfile.

https://www.jamf.com/jamf-nation/my/products

Build new docker image and append version tag.
```
docker build . -t jamfpro:10.42.1 -f ./Dockerfile
```
```
docker compose up --detach
```
set the default authentication plug-in to mysql_native_password or Legacy Password Encryption method using my.cnf bind mount
