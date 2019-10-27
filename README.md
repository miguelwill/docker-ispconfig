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
jerob/docker-ispconfig /start.sh

ISPConfig administration

https://your-ip:8080

ISPConfig login : admin

ISPConfig password : admin

SSH PORT : 2222 ( ssh -p 2222 user@host )

Shell access

docker exec -i -t jerob/docker-ispconfig bash

Reconfigure ISPConfig

ispconfig_update.sh

Webmail

The open source webmail solution Roundcube is available here :

http://your-ip/webmail

PHPMyAdmin

http://your-ip/phpmyadmin

MariaDB login : root

MariaDB password : pass

It is strongly recommended that you change the MariaDB and ISPConfig password as soon as possible
Issues

If you have any issues or suggests, please do not hesitate to write a ticket on the project page https://github.com/jerob/docker-ispconfig/issues
Backup exemple with S3

docker run --volumes-from ispconfig \
-e PASSPHRASE=pass \
-e AWS_ACCESS_KEY_ID=xxxxx \
-e AWS_SECRET_ACCESS_KEY=xxxxx \
-e PARAMS='--allow-source-mismatch \
--full-if-older-than 1W \
--include /var/mail/ \
--include /var/www/ \
--include /var/backup/sql/ \
--include /etc/' \
-e SRC='/' \
-e PARAMS_CLEAN='remove-older-than 3M \
--force --extra-clean' \
-e DEST='s3://xxxxx.amazonaws.com/bucket-name/' \
jerob/docker-duplicity bash /duplicity

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
-p 20:20 \
-p 21:21 \
-p 30000-30009:30000-30009 \
-p 80:80 \
-p 443:443 \
-p 8080:8080 \
-p 53:53 \
-p 2222:22 \
jerob/docker-ispconfig:beta /start.sh
