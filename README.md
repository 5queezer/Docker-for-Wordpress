# Docker for Wordpress

This is a dockerized solution for Wordpress which is based on Bitnami images. It has an Apache webserver with MariaDB. The database can be accessed via Adminer at the port 8080.

Following images will be used:
- bitnami/wordpress with xdebug enabled
- bitnami/mariadb with an empty password
- adminer

## Installation

Installation requirements:

- docker installed
- available ports 80 and 8080

### .env file

Copy the `.env.sample` to `.env` and set the username and the database name.

### Run the Container

Start the containers with `docker-compose up -d`. This will download and build them if it is the first time. New directories `src/`, `etc/apache` and `etc/php` will be created.

### Install Wordpress core files

Download and extract your wordpress files into `wp/wordpress`. This is the Apache server root folder.

### Configure your wordpress installation

Adapt your `wp-config.php` to match the settings in the `.env` file. Remember that the password is empty. The database hostname in `wp-config.php` should be changed to `mariadb`, which corresponds to the the service name in `docker-compose.yml`

## Useful commands

Run these commands in the root folder of that repository.

| Command                  | Effect                                                                                              |
|--------------------------|-----------------------------------------------------------------------------------------------------|
| `docker-compose up -d`   | Starts the containers demonized.                                                                    |
| `docker-compose build`   | Downloads and builds the containers.                                                                |
| `docker-compose down`    | Stops all container                                                                                 |
| `docker-compose ps`      | Shows all running container with their assigned ports                                               |
| `docker-compose exec wordpress bash`  | Opens a console in the container                                                       |
