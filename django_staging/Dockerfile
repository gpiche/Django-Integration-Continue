# This file is a template, and might need editing before it works on your project.
FROM ubuntu:17.10

MAINTAINER Guillaume Piché et Alexandra Bacon-Vollant version: 0.1

#Mise à jour du système
RUN apt-get update

#Installation de python3 et de pip3
RUN apt-get -y install python3
RUN apt-get install -y python3-pip

#Installation de git 
RUN apt-get -y install git

# Installation de postegresql.
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        postgresql-client \
    && rm -rf /var/lib/apt/lists/*

#Installation de django
RUN pip3 install django

#Création du workspace
RUN mkdir -p /django_project
WORKDIR /django_project

#Volume
VOLUME /root/.ssh

# Pour django
EXPOSE 8000

# Part le serveur 
ENTRYPOINT git clone git@gitlab.com:gpiche/project_GP-ABV.git && cd project_GP-ABV/DjangoWeb  && python3 manage.py runserver 0.0.0.0:8000 

