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
   - Ubuntu 16.04:
   ```
     - curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
     - sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
     - sudo apt-get update
     - sudo apt-get install -y docker-ce
     - docker --version
   ```  
2. Clone this public repository:
   `git clone git://github.com/pablodonayre/docker-slim-framework.git`

3. Go inside **myappname** and execute (to download vendor directory): `composer install`

4. Execute the following commands:

   -To know the ip of the machine: `docker-machine ip`

   -To execute the docker-compose file: `docker-compose up -d`

5. At this point, the containers should be running, check them with: `docker ps -a` 

6. To know the ip of the machine (For Windows): `docker-machine ip`

7. Search for that ip:8085 in your browser (At this point the Slim Project should be running :sunglasses:)

8. Search for the ip:8090 for phpMyadmin (credentials in **docker-compose.yml**)

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
