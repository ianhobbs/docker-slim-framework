# docker-slim-framework
Slim Framework ready to use (with docker containers)

## TUTORIALS:
	This repository was prepared with the information in the following links:
  https://morgandavison.com/2016/10/01/set-up-slim-framework-on-docker/
  https://github.com/slimphp/Slim-Skeleton

  Notes:
    You must maintain the directoy structure as follows: /var/www/html
    "html" folder is needed
    If not you will get error https://github.com/moby/moby/issues/26855

# INSTRUCTIONS:

	1) Install Docker:
		Windows: https://www.docker.com/community-edition
		
		Ubuntu 16.04:
		a) curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
		b) sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
		c) sudo apt-get update
		d) sudo apt-get install -y docker-ce
		e) docker --version

	2) Clone this public repository:
		git clone git://github.com/pablodonayre/docker-slim-framework.git

		Inside myappname (to download vendor directory): composer install

	3) Execute the following commands:
		-To know the ip of the machine: docker-machine ip
		-To execute the docker-compose file: docker-compose up -d

	4) To know the ip of the machine: docker-machine ip

	5) Search for that ip in your browser (Slim Project running)

	6) Search for the ip:8080 for phpMyadmin (credentials in docker-compose.yml)

Docker usefull commands:
If you are using Ubuntu, you need to add sudo at the begining of all the docker commands :
	# To list all containers:
	docker ps -a

	# To stop all containers
	docker stop $(docker ps -a -q)
	Ubuntu example: sudo docker stop $(sudo docker ps -a -q)

	# To remove all containers
	docker rm $(docker ps -a -q)

	# To remove all images of the disk (force to remove). Warning !
	docker rmi -f $(docker images -q)

	$ To go inside the container:
	docker exec -it <name-of-the-container> bash

To use latest versions of containers:
For example, you only need to modify te following, inside docker-compose.yml: 
Use "image: mysql:latest" instead of "image: mysql:5.7.20", or specify the version you need (Review Docker Hub for Tags)

To update Slim-Skeleton:
Slim framework comes "ready to use" in this repository (from Akrabat repository), but if you need to update your slim-skeleton, or maybe change it:

The "myappname" directory was created as follows:
# Akrabat: https://github.com/akrabat/slim3-skeleton
	composer create-project --no-interaction --stability=dev akrabat/slim3-skeleton myappname

Also, you can use:	
# Oficial: https://github.com/slimphp/Slim-Skeleton
	composer create-project slim/slim-skeleton myappname
