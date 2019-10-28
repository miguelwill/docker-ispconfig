ISPConfig is an Open source, BSD-licensed, hosting control panel for Linux, designed to manage Apache, BIND, FTP, and databases, supporting many Linux distributions.

ISPConfig 3.1.15

Official website https://www.ispconfig.org

ISPConfig 3 Screenshots https://www.ispconfig.org/ispconfig/screenshots/

Start ISPConfig

docker run --name ispconfig \
-e MAILMAN_EMAIL_HOST=test.com \
-e MAILMAN_EMAIL=test@test.com \
-e MAILMAN_PASS=pass \
-d \
-v $(pwd)/mysql:/var/lib/mysql \
-v $(pwd)/www:/var/www \
-v $(pwd)/mail:/var/mail \
-v $(pwd)/ispconfig:/usr/local/ispconfig \
-p 20:20 \
-p 21:21 \
-p 30000-30009:30000-30009 \
-p 80:80 \
-p 443:443 \
-p 8080:8080 \
-p 53:53 \
-p 2222:22 \
-p 110:110 \
-p 143:143 \
-p 993:993 \
-p 995:995 \
miguelwill/docker-ispconfig /start.sh

ISPConfig administration

https://your-ip:8080

ISPConfig login : admin

ISPConfig password : admin

SSH PORT : 2222 ( ssh -p 2222 user@host )

Shell access

docker exec -i -t miguelwill/docker-ispconfig bash

Reconfigure ISPConfig

ispconfig_update.sh

Webmail

The open source webmail solution Roundcube is available here :

http://your-ip/webmail

PHPMyAdmin

http://your-ip/phpmyadmin

MariaDB login : root

MariaDB password : kl32j42l2kj34

It is strongly recommended that you change the MariaDB and ISPConfig password as soon as possible
Issues

If you have any issues or suggests, please do not hesitate to write a ticket on the project page https://github.com/miguelwill/docker-ispconfig/issues

ISPConfig Beta

Recommended for test setups only!

If you like to try out the pre-release of an upcoming 3.1 version, download it with this command:

docker run --name ispconfig \
-e MAILMAN_EMAIL_HOST=test.com \
-e MAILMAN_EMAIL=test@test.com \
-e MAILMAN_PASS=pass \
-d \
-v $(pwd)/mysql:/var/lib/mysql \
-v $(pwd)/www:/var/www \
-v $(pwd)/mail:/var/mail \
-v $(pwd)/ispconfig:/usr/local/ispconfig \
-p 20:20 \
-p 21:21 \
-p 30000-30009:30000-30009 \
-p 80:80 \
-p 443:443 \
-p 8080:8080 \
-p 53:53 \
-p 2222:22 \
-p 110:110 \
-p 143:143 \
-p 993:993 \
-p 995:995 \
miguelwill/docker-ispconfig:beta /start.sh
