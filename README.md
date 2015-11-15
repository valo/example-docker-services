# An example microservice app running with docker-compose

This is an example microservice application that is running with [docker-compose](https://docs.docker.com/compose/).

The app consists of the following components:
* Frontend built with sinatra, which allows submitting source codes
* A PostgreSQL database used by the frontend for storing data
* A Grader microservice which grades the sources codes and returns a score for each of them
* A [RabbitMQ](https://www.rabbitmq.com/) server used for communication between the frontend and the grader
* Background processes
  ** One in the grader service, which reads source codes from RabbitMQ and submits its score back in the RabbitMQ
  ** One in the frontend service, which reads the scores of the source codes and stores them in the PostgreSQL database
  
The app is fairly simple, but in order to run it you need one database server, one rabbitmq server, one app server for the sinatra app and two background processes. With docker-compose all this can be run with a single command:

```bash
$ docker-compose up
```
  
Read more on my blog: https://www.valentinmihov.com/2015/11/15/microservices-dev-environment-with-docker/
