# docker-wordpress

## requirements 
- new relic license key
-docker 

## Contents
This project generates a wordpress blog with mysql database and phpmyadming, adding a new relic apm agent on the wordpress blog.
- mysql version : 8
- wordpress version : latest
- php myadmin version: latest
- new relic apm agent : 9.9.0.260

## Usage
start docker: 

- clone the git repository
- run docker-compose -d up  ##this will run docker in dettached mode.

to stop docker:
- docker-compose down.

## Other
- This docker file sets the ports of your wordpress page to be exposed in 8084
- This docker file sets the ports of your wordpress page to be exposed in 8083
- User/password for mysql and wordpress are not safe, if you are planning to expose this to the world you should probably change them.

