# centralize-log-with-EFK
Centralize spring boot application log with Elastic FluentD and Kibana

The purpose of this project is to dockerize a simple spring-boot project an run it together with EFK ( Elasticsearch,Fluentd and Kibana) stack in diferent containers on minikube

## Components

* spring-boot-app: simple spring boot application that send some logs and errors to the container
* fluentd: Unify all facets of processing log data: collecting, filtering, buffering, and outputting logs across multiple sources and destinations. In our case, it will receive logs from the microservice format and forward/post them to elasticsearch.
* elastic-search: Search engine and a full-text, distributed NoSQL database.
* kibana: Front-end for elastic-search.elastic-search: Search engine and a full-text, distributed NoSQL database.

## Pre-requisitos:

* java 11
* docker
* minikube

## Spring boot project

### Create image and push it to docker image

```cd /app```

```docker build -t my-app .```

## Deploy to Kubernetes

### Create a Secret docker-registry (in case of private image)

  DOCKER_REGISTRY_SERVER=docker.io
  DOCKER_USER=your dockerID, same as for `docker login`
  DOCKER_EMAIL=your dockerhub email, same as for `docker login`
  DOCKER_PASSWORD=your dockerhub pwd, same as for `docker login`

  kubectl create secret docker-registry myregistrysecret \
  --docker-server=$DOCKER_REGISTRY_SERVER \
  --docker-username=$DOCKER_USER \
  --docker-password=$DOCKER_PASSWORD \
  --docker-email=$DOCKER_EMAIL
  
  


