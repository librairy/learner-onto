# Ontology Learner [![Release Status](https://travis-ci.org/librairy/learner-onto.svg?branch=master)](https://travis-ci.org/librairy/learner-onto) [![Dev Status](https://travis-ci.org/librairy/learner-onto.svg?branch=develop)](https://travis-ci.org/librairy/learner-onto) [![Doc](https://raw.githubusercontent.com/librairy/resources/master/figures/interface.png)](https://rawgit.com/librairy/learner-onto/doc/report/index.html)

Build an ontology for a given domain. 

It extends the [epnoi](https://github.com/epnoi/epnoi) project, a system which identifies the most relevant terms and discovers hypernym relations between them for a given domain.

## Get Started!

A prerequisite to consider is to have installed [Docker-Compose](https://docs.docker.com/compose/) in your system.

You can run this service in a isolated way (see *Distibuted Deployment* section) or as extension of the [explorer](https://github.com/librairy/explorer).
In that case, add the following services to the existing `docker-compose.yml` file:

```yml
learnerOnto:
  container_name: learnerOnto
  image: librairy/learner-onto
  links:
      - column-db
      - document-db
      - graph-db
      - event-bus
```

and then, deploy it by typing:

```sh
$ docker-compose up
```
That's all!! **librairy Ontology learner** should be run in your system now along with **librairy explorer**.

## Distributed Deployment

Instead of deploy all containers as a whole, you can deploy each of them independently. It is useful to run the service in a distributed way deployed in several host-machines.

- **Ontology-Learner**:  

    ```sh
    $ docker run -it --rm --name learnerOnto librairy/learner-onto
    ````

Remember that by using the flags: `-it --rm`, the services runs in foreground mode. Instead, you can deploy it in background mode as a domain service by using: `-d --restart=always`