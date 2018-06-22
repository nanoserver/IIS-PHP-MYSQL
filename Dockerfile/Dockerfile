# Dockerfile for Nano Server with IIS Role, PHP and MySQL.

FROM nanoserver/iis-php

MAINTAINER nanoserver.es@gmail.com

ADD https://dev.mysql.com/get/Downloads/MySQL-5.7/mysql-5.7.22-winx64.zip mysql.zip
RUN powershell -command \
    Expand-Archive -Path c:\mysql.zip -DestinationPath C:\ ; \
    ren C:\mysql-5.7.22-winx64 C:\MySQL ; \
    New-Item -Path C:\MySQL\data -ItemType directory ; \
    C:\MySQL\bin\mysqld.exe --initialize --console --explicit_defaults_for_timestamp ; \
    C:\MySQL\bin\mysqld.exe --install ; \
    Start-Service mysql ; \
    Remove-Item c:\mysql.zip -Force
    
ENV MYSQL C:\\MySQL
RUN setx PATH /M %PATH%;C:\MySQL\bin
