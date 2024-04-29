#Devops


## Running Hello World in Docker

> Problem

You have access to a Docker host and want to run your first container. You want to learn the various life cycles of a container. As an example, you want to run a container and echo Hello World in it.

> Solution

Typing docker at the prompt returns the usage of the docker command:

`$ docker`

Usage: `docker [OPTIONS] COMMAND [arg...]`

A self-sufficient runtime for linux containers.

```
Unable to find image 'busybox' locally
busybox:latest: The image you are pulling has been verified
511136ea3c5a: Pull complete
df7546f9f060: Pull complete
e433a6c5b276: Pull complete
e72ac664f4f0: Pull complete
Status: Downloaded newer image for busybox:latest
hello world
```

==Containers are based on images==. An image needs to be passed to the `docker run` command. In the preceding example, you specify an image called busybox. Docker does not have this image locally and pulls it from a public registry. A registry is a catalog of Docker images that the Docker client can communicate with and download images from. Once the image is pulled, Docker starts a container and executes the echo hello world command. Congratulations—you ran your first container.

---

## Knowing the Difference Between Containers and Virtual Machines

In comparison, with `containers`, the ==sharing of the host OS’s kernel== with the application means that the overhead of an additional OS is removed.

## Dockerfile

A Dockerfile is a set of instructions that tells Docker how to build an image. A typical Dockerfile is made up of the following:

- A `FROM` instruction that tells Docker what the base image is
- An `ENV` instruction to pass an environment variable.
- A `RUN` instruction to run some shell commands (for example, install-dependent programs not available in the base image).
- A `CMD` or an `ENTRYPOINT` instruction that tells Docker which executable to run when a container is started.


## Docker Image

`Docker image` is a ==read-only template== that forms the foundation of your application Docker images are created using a `series of commands`, known as instructions, in the `Dockerfile`. 

Breakdown of a `.Dockerfile`

- A Docker image starts with a ==base image==, such as Ubuntu.
- On top of this image, we can add build our ==application stack== adding the packages as and when required.

> Notes:

On the advanced scale, to keep the image size as low as possible, we can also start with slim packages, such as `Alpine` or even Scratch, which is Docker’s reserved, minimal starting image for building other images.


Every Docker image has an `associated tag`. Tags typically include `names` and `version labels`. While it is not mandatory to associate a version tag with a Docker image name, these tags make it easier to roll back to previous versions. Without a tag name, Docker must fetch the image with the latest tag. You can also provide a tag name to force-fetch a tagged image.

## Docker Container

A Docker image, when it’s run in a host computer, spawns a process with its own namespace, known as a Docker container.

The `main difference between` a Docker `image` and a `container` is the presence of a thin read/write layer known as the ==container layer==. Any changes to the filesystem of a container, such as writing new files or modifying existing files, are done to this writable container layer than the lower layers.

==An important aspect to grasp== is that when a container is running, the changes are applied to the container layer and when the container is stopped/killed, the container layer is not saved. Hence, all changes are lost. 

This aspect of containers is not understood very well and for this reason, stateful applications and those requiring persistent data were initially not recommended as containerized applications. However, with `Docker Volumes`, there are ways to get around this limitation.

## Bind Mounts and Volumes

Docker provides different ways to mount data into a container from the Docker host: 

- volumes,
- bind mounts, & 
- tmpfs volumes.

While `tmpfs volumes` are stored in the host system’s memory only, `bind mounts` and `volumes` are stored in the host filesystem



---

## Docker Engine
Docker Engine is the core part of Docker. Docker Engine is a client-server application that provides the platform, the runtime, and the tooling for building and managing Docker images, Docker containers, and more. Docker Engine provides the following:

- Docker daemon
- Docker CLI
- Docker API


### Docker Daemon

The Docker daemon is a `service` that ==runs in the background of the host computer== and handles the heavy lifting of most of the Docker commands. The daemon listens for API requests for creating and managing Docker objects, such as `containers`, `networks`, and `volumes`.

### Docker CLI

Docker CLI is the primary way that you will interact with Docker. Docker CLI exposes a set of commands that you can provide. The Docker CLI forwards the request to Docker daemon, which then performs the necessary work.

While the Docker CLI includes a huge variety of commands and sub-commands, the most common commands that we will work with in this book are as mentioned:

```bash title="bash"
$ docker build
$ docker pull
$ docker run
$ docker exec
```

### Docker API

Docker also provides an API for interacting with the Docker Engine. This is particularly useful if there’s a need to create or manage containers from within applications. 

---

## Docker Compose

Docker Compose is a tool for defining and `running multi-container applications`. Much like how Docker allows you to build an image for your application and run it in your container, Compose use the same images in combination with a definition file (known as the compose file) to build, launch, and run multi-container applications, including dependent and linked containers.

The most common use case for Docker Compose is to run applications and their dependent services (such as databases and caching providers) in the same simple, streamlined manner as running a single container application.

---

## Volume

Docker volumes are the current recommended method of persisting data stored in containers. Volumes are completely managed by Docker and have many advantages over bind mounts:


### Docker Volume Subcommands

Docker exposes the Volume API as a series of subcommands.

```bash title="bash"
$ docker volume create

$ docker volume inspect

$ docker volume ls

$ docker volume prune

$ docker volume rm
```

---

## Hands on Docker `Commands`

```bash title="bash"
# Make sure the docke in installed
$ docker info

# Working with Docker Images
# listing of the images available locally
$ docker image ls

# docker inspect command provides a lot of information about the image
$ docker image inspect hello-world

# Of importance are the image properties Env, Cmd, and Layers,
# which tell us about these environment variables.

# Env
$ docker image inspect hello-world | jq .[].Config.Env

# startup command on the container
$ docker image inspect hello-world | jq .[].Config.Cmd

# layers associated with the image
$ docker image inspect hello-world | jq .[].RootFS.Layers

#
$ docker image inspect nginx | jq .[].Config.ExposedPorts
```