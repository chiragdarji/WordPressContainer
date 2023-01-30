# WordPressContainer

WordPress Container on Docker

# Step #1

Let's try to install Wordpress component separately. 

1. Mysql
2. Wordpress
3. PhpMyAdmin

## MySQL

`docker run --name some-mysql --network some-network -e MYSQL_ROOT_PASSWORD=password -d mysql:latest`

1. `docker run`: This is the main command to run a Docker container.

2. `--name some-mysql`: This option sets the name of the container to some-mysql.

3. `--network some-network`: This option connects the container to the Docker network named some-network.

4. `-e MYSQL_ROOT_PASSWORD=password`: This option sets an environment variable MYSQL_ROOT_PASSWORD to the value password. This variable is used by the MySQL image to set the password for the root user of the MySQL database.

5. `-d mysql:latest`: This option specifies the image to use for the container. The image name is mysql and the tag is latest, meaning the latest version of the image will be used. The -d option runs the container in the background.

6. `mysql:latest`: This is the image name and tag that the Docker container is based on. The mysql image provides a MySQL database server, and the latest tag specifies the most recent version of the image.

## PhpMyAdmin

`docker run --name some-phpmyadmin --network some-network -p 8080:80 -d phpmyadmin/phpmyadmin`

1. `docker run`: This is the main command to run a Docker container.

2. `--name some-phpmyadmin`: This option sets the name of the container to some-phpmyadmin.

3. `--network some-network`: This option connects the container to the Docker network named some-network.

4. `-p 8080:80`: This option maps a port on the host to a port in the container. The 8080 port on the host is mapped to the 80 port in the container. This allows you to access the container's web application, such as phpMyAdmin, through a web browser on the host using http://localhost:8080.

5. `-d phpmyadmin/phpmyadmin`: This option specifies the image to use for the container. The image name is phpmyadmin/phpmyadmin, which is the official phpMyAdmin image from the Docker repository. The -d option runs the container in the background.

6. `phpmyadmin/phpmyadmin`: This is the image name that the Docker container is based on. The phpmyadmin/phpmyadmin image provides a web-based interface for managing MySQL databases, and is specifically designed for use with the MySQL database.


## Wordpress

`docker run --name some-wordpress --network some-network -e WORDPRESS_DB_PASSWORD=password -p 80:80 -v /my/custom/path/wp-content:/var/www/html/wp-content -d wordpress:latest`

1. `docker run`: This is the main command to run a Docker container.

2. `--name some-wordpress`: This option sets the name of the container to some-wordpress.

3. `--network some-network`: This option connects the container to the Docker network named some-network.

4. `-e WORDPRESS_DB_PASSWORD=password`: This option sets an environment variable WORDPRESS_DB_PASSWORD to the value password. This variable is used by the WordPress image to set the password for the WordPress database.

5. `-p 80:80`: This option maps a port on the host to a port in the container. The 8080 port on the host is mapped to the 80 port in the container. This allows you to access the container's web application, such as WordPress, through a web browser on the host using http://localhost:80.

6. `-v /my/custom/path/wp-content:/var/www/html/wp-content`: This option mounts a volume from the host to the container. The host path /my/custom/path/wp-content is mounted as the container path /var/www/html/wp-content. This allows you to persist the WordPress content and customizations outside of the container, even if the container is deleted or recreated.

7. `-d wordpress:latest`: This option specifies the image to use for the container. The image name is wordpress and the tag is latest, meaning the latest version of the image will be used. The -d option runs the container in the background.

8. `wordpress:latest`: This is the image name and tag that the Docker container is based on. The wordpress image provides a WordPress web application, and the latest tag specifies the most recent version of the image.