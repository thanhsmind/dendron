---
type: programing 
---
# Wordpress Install with Docker

## Defining Services with Docker Compose
**db service**

```yml
version: "3.7"
  
services:

	db:
		image: mysql:5.7
		container_name: db
		restart: unless-stopped
		environment:
			MYSQL_DATABASE: db
			MYSQL_USER: exampleuser
			MYSQL_PASSWORD: examplepassword
			MYSQL_RANDOM_ROOT_PASSWORD: "ROOTPASS"
		volumes:
			- db:/var/lib/mysql
		networks:
			app-network

	wordpress:
		depends_on:
			- db
		image: wordpress:5.8.1-php7.4-fpm-alpine
		container_name: wordpress
		restart: unless-stopped
		environment:
			WORDPRESS_DB_HOST: db
			WORDPRESS_DB_USER: thetalentproweb
			WORDPRESS_DB_PASSWORD: thetalentprocamcui
			WORDPRESS_DB_NAME: webthetalentpro
		volumes:
			- wordpress:/var/www/html
			- ./themes/dt-the7:/var/www/html/wp-content/themes/dt-the7/
			- ./plugins:/var/www/html/wp-content/plugins/
		networks:
			- app-network

volumes:
	wordpress:
	db:
	
networks:
	app-network:
	driver: bridge
```

wordpress sẽ tự động lưu code của framework trong thư mục wordpress. các thư mục themes, plugins sẽ được mount riêng ra do thường xuyên custom. 