---
type: programing 
---
# [[Wordpress]]
- [[Docker Intall on Ubuntu]]
- [[Wordpress Install with Docker]]
- [[Wordpress Automate deployment using Buddy CI-CD]]
- [[Wordpress setup HTTPS with certbot]]
-   [How to Speed Up WordPress Asset Delivery Using DigitalOcean Spaces CDN](https://www.digitalocean.com/community/tutorials/how-to-speed-up-wordpress-asset-delivery-using-digitalocean-spaces-cdn).
-   [How To Back Up a WordPress Site to Spaces](https://www.digitalocean.com/community/tutorials/how-to-back-up-a-wordpress-site-to-spaces).
-   [How To Store WordPress Assets on DigitalOcean Spaces](https://www.digitalocean.com/community/tutorials/how-to-store-wordpress-assets-on-digitalocean-spaces).
## Defining Services with Docker Compose
```yml
version: "3.7"

# docker-compose.yml
services:
  db:
    image: mysql:5.7
    container_name: db
    restart: unless-stopped
    environment:
      MYSQL_DATABASE: exampledb
      MYSQL_USER: exampleuser
      MYSQL_PASSWORD: examplepass
      MYSQL_RANDOM_ROOT_PASSWORD: "R00rW0rd"
    volumes:
      - db:/var/lib/mysql
    networks:
      - app-network

  wordpress:
    depends_on:
      - db
    image: wordpress:5.8.1-php7.4-fpm-alpine
    container_name: wordpress
    restart: unless-stopped
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
  webserver:
    depends_on:
      - wordpress
    image: nginx:1.21.3-alpine
    container_name: webserver
    restart: unless-stopped
    ports: 
      - "80:80"
      - "443:443"
    volumes:
      - wordpress:/var/www/html
      - ./nginx-conf:/etc/nginx/conf.d
      - certbot-etc:/etc/letsencrypt
      - ./themes/dt-the7:/var/www/html/wp-content/themes/dt-the7/
      - ./plugins:/var/www/html/wp-content/plugins/  
    networks:
      - app-network
  cerbot:
    depends_on:
      - webserver
    image: certbot/certbot
    container_name: certbot
    volumes:
      - certbot-etc:/etc/letsencrypt
      - wordpress:/var/www/html
      - ./themes/dt-the7:/var/www/html/wp-content/themes/dt-the7/
      - ./plugins:/var/www/html/wp-content/plugins/
    command: certonly --webroot --webroot-path=/var/www/html --email thanh@thetalent.pro --agree-tos --no-eff-email --force-renewal -d thetalent.pro -d www.thetalent.pro
volumes:
  wordpress:
  db:
  certbot-etc:

networks:
  app-network:
    driver: bridge   


```