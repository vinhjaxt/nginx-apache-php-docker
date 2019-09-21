# Nginx (alpine) + Apache PHP (mod_php, debian) + MySQL (mariadb, alpine) reverse proxy
- Run: `docker-compose up`
- Nginx static file serve: `./nginx-public_html`
- Apache + PHP: `./public_html`
- MySQL (mariadb) credential at: .env

- http://localhost:8000/nginx-index.html
- http://localhost:8000/apache-index.html
- http://localhost:8000/index.php
- http://localhost:8000/phpinfo.php
- http://localhost:8000/phpmyadmin

@vinhjaxt