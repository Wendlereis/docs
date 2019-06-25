# Getting started with docker

## Create a Dockerfile

```Dockerfile
  FROM node:6

  # Set the working directory in the container to /app
  WORKDIR /app

  # Copy the current directory contents into the container at /app
  ADD . /app

  # Make the container's port 80 available to the outside world
  EXPOSE 80

  # Run app.js using node when the container launches
  CMD ["node", "app.js"]
```

## Build the docker image

```sh 
$ docker build -t node-app:0.1 .
```

## Run docker images

The `-p` flag maps the container's port to your machine's port. In this case your 4000 port were maped to the 80 port on the container.

```sh 
$ docker run -p 4000:80 --name my-app node-app:0.1
```
## Run docker image with mapped volume

```sh 
$ docker run -p 8080:8080 -v $PWD:/usr/src/app -d node-app:0.1
```

The variable `$PWD` in command above, has the absolute path of the current opened directory

## Access bash terminal inside the container

```sh
$ docker exec -it [container_id] bash
```

## Publish the image to the Google Cloud Registry

```sh
$ docker tag node-app:0.1 gcr.io/[project-id]/node-app:0.1

$ docker push gcr.io/[project-id]/node-app:0.1
```

## Remove images from local registry

```sh
$ docker rmi node-app:0.2 gcr.io/[project-id]/node-app node-app:0.1
```


[<< Menu](../README.md)