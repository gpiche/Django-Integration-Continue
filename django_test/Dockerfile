# This file is a template, and might need editing before it works on your project.
FROM ubuntu:17.10

MAINTAINER Guillaume Piché et Alexandra Bacon-Vollant version: 0.1

#Mise à jour du système
RUN apt-get update

#Installation de python3 et pip3
RUN apt-get -y install python3
RUN apt-get install -y python3-pip

#Installation de git
RUN apt-get -y install git

# Installation de postegresql
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        postgresql-client \
    && rm -rf /var/lib/apt/lists/*

#Installation de django
RUN pip3 install django

#Création du workspace
RUN mkdir -p /django_project
WORKDIR /django_project

#Argument utilisé par jenkins
ARG branch

#Volume
VOLUME /root/.ssh

# Pour Django
EXPOSE 8000

#Par les test du projet
ENTRYPOINT git clone git@gitlab.com:gpiche/project_GP-ABV.git && cd  project_GP-ABV/DjangoWeb && git checkout $branch && python3 manage.py test

