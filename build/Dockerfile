#!/bin/bash
# Autor:........Rafael Ricardo Reyes Sandoval
# Propósito:....Definir la imagen que realiza el scaneo de protocolos SSL que soporta un host por los puertos 443 y 8443

# Imagen base desde la que se crea la herramienta
FROM mysql:latest

# Nombre del propietario
MAINTAINER Rafael Ricardo Reyes Sandoval

# Copia el script ".sql" para la creación de la tabla
COPY ./sql /docker-entrypoint-initdb.d/

# Instalar dependencias necesarias
RUN apt-get update -qqy && \
    apt-get install -y nmap wget && \
    wget -O /usr/local/bin/ssl_scan https://raw.githubusercontent.com/rafaelreyescv/script_ssl_escaner/main/ssl_scan && \
    chmod +x /usr/local/bin/ssl_scan

# Volúmenes con los datos relevantes para el servicio
VOLUME ["/var/lib/mysql","/mnt/escaner_ssl"]
