# docker-slim-framework
Slim Framework ready to use (with docker containers)

## TUTORIALS:
This repository was prepared with the information in the following links:

[Set up Slim Framework on Docker](https://morgandavison.com/2016/10/01/set-up-slim-framework-on-docker)

[Slim Framework 3 Skeleton Application](https://github.com/slimphp/Slim-Skeleton)

**Notes:**
    You must maintain the directoy structure as follows: **/var/www/html** ("html" folder is needed)
    If not, you will get error [oci runtime error](https://github.com/moby/moby/issues/26855)

## INSTRUCTIONS:
1. Install Docker:
   - Windows 8/10: https://www.docker.com/community-edition
   - Ubuntu 16.04 (64 bits): https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/#os-requirements
   
2. Clone this public repository:
   `git clone git://github.com/pablodonayre/docker-slim-framework.git`

3. Go inside **myappname** and execute (to download vendor directory): `composer install`
   - Error: "mbstring not found". To Fix try: `sudo apt-get install php7.0-mbstring`
   
   ![mbstring](https://user-images.githubusercontent.com/17578664/34341464-dc0f2668-e976-11e7-9516-40057a267569.jpg)
   
   - Error: "dom not found". to fix try: `sudo apt-get install php7.0-xml` and then `sudo apt-get install zip unzip php7.0-zip`
   
   ![dom](https://user-images.githubusercontent.com/17578664/34341576-e40af570-e978-11e7-8799-9b60a7dc9eac.jpg)

4. Execute the following commands (Get out of **myappname** / Need to be at the level of **docker-compose.yml**):

   -To know the ip of the machine: `docker-machine ip`

   -To execute the docker-compose file: `docker-compose up -d`

5. At this point, the containers should be running, check them with: `docker ps -a` 

6. To know the ip of the machine (For Windows): `docker-machine ip`

7. Search for that ip:8085 in your browser (At this point the Slim Project should be running :sunglasses:)

    NOTE: If you got an error go below to FILE PERMISSIONS (over Ubuntu)

8. Search for the ip:8090 for phpMyadmin (credentials in **docker-compose.yml**)

## File Permissions:
1. If you are using docker over Windows -> You'll not have any error (from step 1 through 8)
2. If you are using docker over linux -> It's probably that on STEP 7 you got an error (PERMISSION ERROR)
   - DEVELOPMENT: For "testing" purposes go at the level of **myappname** and execute: `sudo chmod -R 777` (***Warning*** :exclamation: : Security issues)
   - PRODUCTION: To fix the permission's issues, follow instructions of: [Docker & File Permissions](https://serversforhackers.com/c/dckr-file-permissions)   
        - NOTE 1: For the "PHP container", if you get an error trying to go inside the container using "bash", then, try with "/bin/bash" or "sh"
        - :key: NOTE 2: If don't want to review the Video, you can try the following: Go at the level of **myappname** and execute: `sudo chown -R 82:docker myappname/` (If this do not work, then try the video)
   
## Docker usefull commands:
If you are using Ubuntu 16.04, you need to add `sudo` at the begining of all the **docker** commands:

- To list all containers: `docker ps -a`
- To stop all containers: `docker stop $(docker ps -a -q)`
  - Ubuntu example: `sudo docker stop $(sudo docker ps -a -q)`
- To remove all containers: `docker rm $(docker ps -a -q)`
- To remove all images of the disk (force to remove). ***Warning*** :exclamation: : `docker rmi -f $(docker images -q)`
- To go inside the container: `docker exec -it <name-of-the-container> bash`

## To use latest versions of containers:
For example, you only need to modify te following, inside **docker-compose.yml**: 

Use **image: mysql:latest** instead of **image: mysql:5.7.20**, or specify the version you need (Review Docker Hub for Tags)

## To update Slim-Skeleton:
This Container comes with Slim-Framework "ready to use".

1. The "myappname" directory was created as follows:

   Akrabat: https://github.com/akrabat/slim3-skeleton
   
   RUN: `composer create-project --no-interaction --stability=dev akrabat/slim3-skeleton myappname`

2. Also, you can use:	

   Oficial: https://github.com/slimphp/Slim-Skeleton
   
   RUN: `composer create-project slim/slim-skeleton myappname`
