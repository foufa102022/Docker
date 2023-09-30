#-----------------DÉBUT COUCHE OS----------------
FROM debian:stable-slim
#----------------FIN COUCHE OS----------------

#VARIABLE TEMPORAIRES
ARG APT_FLAGS="-q -y"
ARG DOCUMENTROOT="/var/www/html"

#----------------DÉBUT COUCHE APACHE----------
RUN apt-get update -y && \
    apt-get install ${APT_FLAGS} apache2
#----------------FIN COUCHE APACHE----------

#--------------DÉBUT COUCHE MYSQL-----------
RUN apt-get install ${APT_FLAGS} mariadb-server

COPY data/items.sql /
#--------------FIN COUCHE MYSQL-------------

#-------------DÉBUT COUCHE PHP-------------
RUN apt-get install ${APT_FLAGS} \
    php-mysql \
    php && \
    rm -f ${DOCUMENTROOT}/index.html && \
    apt-get autoclean -y
    	
COPY application ${DOCUMENTROOT}
#--------------FIN COUCHE PHP--------------

#OUVERTURE DE PORT HTTP
EXPOSE 80

#RÉPERTOIRE DE TRAVAIL 
WORKDIR ${DOCUMENTROOT}
#DÉMARRAGE DE SEVICES LORS DE L'EXÉCUTION DE L'IMAGE
ENTRYPOINT service mariadb start && mariadb < /items.sql && apache2ctl -D FOREGROUND



