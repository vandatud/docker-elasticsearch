# VANDA - Elasticsearch Container

_This image is only intended for being part of the VANDA Deap Learning Stack!_ 

Runs [Elasticsearch 5.2.0](https://www.elastic.co/guide/en/elasticsearch/reference/5.2/index.html) on top of the [openjdk/8-jre](https://hub.docker.com/_/openjdk/) with Debian Wheezy as base system.

## Dockerfile

[`vandatud/elasticsearch` Dockerfile](https://github.com/vandatud/docker-elasticsearch/blob/master/Dockerfile)

## How to rebuild an extended image

After pulling this repository and changing the Dockerfile first build the new image locally to test it.
Optionally specify the repository and tag at which to save the new image if the build succeeds.
```
$ docker build -t vandatud/elasticsearch:1.0.1 -t vandatud/elasticsearch:latest -f /path/to/Dockerfile
```

If this Git repository is pushing back to the server, DockerHub will automatically build this image.
For manually push the locally build to the DockerHub use the docker cli.

```
$ docker login
```

```
$ docker push vandatud/elasticsearch:1.0.1
```

## How to use this image

Run a new container instance without

```
$ docker run -d -t -p 9200 -p 9300 --name vanda-elasticsearch_inst vandatud/elasticsearch:latest
```

or with an interactive bash session for inspecting the image.

```
$ docker run --rm -t -i -p 9200 -p 9300 --name vanda-elasticsearch_inst vandatud/elasticsearch:latest -- bash -l
```

```
$ docker ps
CONTAINER ID        IMAGE                           COMMAND             CREATED                  STATUS              PORTS                                              NAMES
e46a689d75a8        vandatud/elasticsearch:latest   "elasticsearch"     Less than a second ago   Up 11 seconds       0.0.0.0:32780->9200/tcp, 0.0.0.0:32779->9300/tcp   vanda-elasticsearch_inst
```

Once the container is running you can open the web interface under the attached host port (i.e. [localhost:32780](http://localhost:32780))

## Tips

For a Elasticsearch cluster use a [Docker composer configuration](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html).


Attach the Docker container with ID or name

```
$ docker exec -i -t vanda-elasticsearch_inst /bin/bash 
```

