# Docker

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- la création d'une image docker  ✔️
- l'éxécution d'un container  ✔️
- l'orchestration de containers avec docker-compose  ✔️


## 💻 J'utilise

### Un exemple personnel commenté ✔️
### Utilisation dans un projet ✔️
### Utilisation en production si applicable✔️
### Utilisation en environement professionnel ✔️

description: Ayant découvert Docker et Docker-compose en entreprise, Je n'ai eu l'occasion de le manipuler uniquement sur des repositories privés c'est pourquoi j'ai décidé de réunir
les questions en un seul exemple épuré de ses données sensibles. L'exemple ci dessous represente un docker-compose.yml permettant la création d'un environnement complet PHP/mysql sur un serveur nginx.
> 
```
version: "2"

services:
  nginx:
    build: docker/nginx
    networks:
      default:
        aliases:
          - ********.****
    volumes_from:
      - php
    volumes:
      - ./cache/nginx/logs:/var/log/nginx:delegated
    links:
      - php
    ports:
      - 80:80


  php:
    build: docker/php
    expose:
      - 9001
    ports:
      - 9000:9000
    volumes:
      - cache/composer:/var/www/.composer/cache:cached
      - .:/var/www/html:cached
    links:
      - db
      - elasticsearch
      - memcached
      - mailhog
    environment:
       MH_SENDMAIL_SMTP_ADDR: 'mailhog:1025'


  db:
    build: docker/db
    ports:
      - 3306:3306
    volumes:
      - ./cache/db:/var/lib/mysql:delegated
      - ./db/entrypoint:/docker-entrypoint-initdb.d:cached
    environment:
      MYSQL_ROOT_PASSWORD: '****'
      MYSQL_DATABASE: '*****'
      MYSQL_USER: '******'
      MYSQL_PASSWORD: '******'


  elasticsearch:
    image: elasticsearch:5.6
    ports:
      - 9200:9200
    environment:
      - xpack.security.enabled=false
    volumes:
      - ./cache/elasticsearch:/usr/share/elasticsearch/data:delegated


  memcached:
    image: memcached:1.5.1
    ports:
      - 11211:11211


  mailhog:
    image: mailhog/mailhog
    ports:
      - 1025:1025
      - 8025:8025
```


## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️
