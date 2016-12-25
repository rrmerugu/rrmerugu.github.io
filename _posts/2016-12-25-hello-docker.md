---
layout: post
title: Hello Docker - my docker notes
---


[Docker](https://www.docker.com) as the website homepage says 
`is the world’s leading software containerization platform`. 
Dockers and container tech has become a common practise in the software development. 
I tried it and fell in love with this for many reasons.  The prime reason 
is it is an open-source project. Long hail opensource developers. 


<!--/excerpt-->

So I've experimenting on the scenrios in which i might need to use docker containers. 
I mostly work with Django, but the technical stack varies from simple 
`Django + sqlite` to `Django + postgres + redis + celery` and more. 

Let me share my reasons of falling in love with Docker. 

### 1.Maintaining the consistency in the version of the tools used by every developer
Although installation is a one time affair. Maintaining the consistency in the version of the tools used by every developer
of the project is a challenge. Dockers solve that easily. 

### 2.No re-installation and reconfigure headaches
Docker comes with `docker-compose.yml` file which will do all your dirty configuration headaches.

### 3.Integrating multiple tools is not hard
Docker's `docker-compose.yml` makes it easy to install the required tech stack images. 

Example: If you want to build a `Django + Postgres`  container. All you do is 


``` 
# docker-compose.yml

version: "2"

services:
  db:
     image: postgres
  web:
    build: .
    container_name: django_postgres
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - ./hello_django:/hello_django
    ports:
      - "8000:8000"
    depends_on:
      - db
```


```
# Dockerfile 

FROM python:2.7
ENV PYTHONUNBUFFERED 1
RUN mkdir /hello_django
WORKDIR /hello_django
ADD ./hello_django/ /hello_django/
RUN pip install -r requirements.txt
```

Execute `docker-compose build` to build the container or `docker-compose up -d` to 
run the application. You should be able to access the django server running and available 
on the url `http://{your-docker-ip}:8000` in my case it's `http://192.168.99.100:8000`

## 4.Above all, it's open-source
It's an opensource project and that makes it more awesome - the developers, 
tutorials and active community makes it more powerfull than other container 
technology.

 
All the docker scenarios i've experimented were published in `https://github.com/rrmerugu/hello-docker`


Try it out. All the very best :)
