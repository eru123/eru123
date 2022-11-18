# Docker Documentation (Simplified)

## Docker Image

Docker image is a read-only template with instructions for creating a Docker container. Docker image is a set of file system changes and the corresponding execution parameters for use within a container runtime. Docker image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.

It can be referred to as a "container image", "image", "template" or "snapshot" of a state of an operating system.

### Create Docker Image

To create a Docker image, you need to create a Dockerfile. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. Using docker build users can create an automated build that executes several command-line instructions in succession.

First, create Dockerfile in the root directory of your project. Then, add the following content to the Dockerfile:

```dockerfile
# Base image can be a fresh installation 
# of Ubuntu or an existing image or a 
# container that has your application and
# all its dependencies installed on top 
# of it. 
# NOTE: It is recommended to use a specific
# version of a base image to avoid any
# unexpected changes in the base image.

# I use the latest build of ubuntu as base image.
FROM ubuntu:latest as base

# add docker image metadata
LABEL maintainer="Your Name <Jericho>"
LABEL version="1.0"
LABEL description="This is a sample Dockerfile."
LABEL website=""
LABEL email=""
LABEL license="MIT"

# ARG is used to define a variable that
# users can pass at build-time to the 
# builder with the docker build command
# using the --build-arg <varname>=<value> flag.

# ARG with no default value
ARG HOST

# ARG with default value
ARG API_PORT=8080

# ARG sample usage
ENV API_URL=http://$HOST:$API_PORT

# or with brackets
ENV API_URL=http://${HOST}:${API_PORT}

# Environment variables are used to configure
# the runtime environment for the container
# process. They are not persisted in the image
# and are not available to the build process.
# They are used to pass information to the
# container process at runtime.

# ENV vs ARG
# ENV is used to set environment variables
# that are available to the container process
# at runtime. ARG is used to set variables
# that are only available to the build process.

# If you know the OS commands you can take
# advantage of the RUN command to execute
# them. This is useful for installing
# dependencies and other OS level commands.
RUN apt-get update && apt-get install -y nodejs npm

# Create app directory
RUN mkdir -p /usr/src/app

# Working directory is the directory where
# all the commands will be executed. It can
# be changed using the WORKDIR command.
# Current workdir can be accessed using
# the $PWD environment variable. or the
# `.` character.
# Example: `RUN ls $PWD` or `RUN ls .` to
# list the files in the current directory.

# Set the working directory to /usr/src/app
WORKDIR /usr/src/app

# Normally, you put the dockerfile in the
# root directory of your project. So, you
# can copy the entire project to the
# working directory using the COPY command.

# Copy command takes two arguments. The
# first argument is the source file or
# directory from the project directory.
# The second argument is the destination
# directory in the container.

# Copy the current directory contents into
# the container at /usr/src/app
COPY . .

# The above code can be written as:
COPY ./ /usr/src/app

# You can also copy files from a remote
# location using the ADD command. The ADD
# command can also extract files from a
# tar file. The ADD command is more
# powerful than the COPY command.

# ADD example
ADD https://example.com/file.tar.gz /usr/src/app

# The EXPOSE command informs Docker that
# the container listens on the specified
# network ports at runtime. You can specify
# whether the port listens on TCP or UDP,
# and the default is TCP if the protocol is
# not specified.

# EXPOSE example
EXPOSE 8080/tcp

# The CMD command provides defaults for
# an executing container. There can only be
# one CMD command in a Dockerfile. If you
# list more than one CMD then only the last
# CMD will take effect.

# CMD example
CMD ["node", "server.js"]

# The ENTRYPOINT command allows you to
# configure a container that will run as an
# executable. You can specify parameters to
# ENTRYPOINT which will always be passed to
# it. You can also override the default
# parameters using the command line when
# docker container is run.

# ENTRYPOINT example
ENTRYPOINT ["node", "server.js"]
```

### Build Docker Image

To build a Docker image, run the following command in the root directory of your project:

```bash
# build docker image (format)
docker build -t <image-name>[:<tag>] <path-to-dockerfile> [--build-arg <varname>=<value>] [--no-cache]

# Build docker image with username, image name and tag
docker build -t <username>/<image-name>:<tag> .

### Build Docker Image with image name and and arguments, default tag is latest
docker build -t <image-name> . --build-arg HOST=<host-name>

### Build Docker Image with image name, default tag is latest if not specified
docker build -t <image-name> .
```

### Run Docker Image

To run a Docker image, run the following command:

```bash
# run docker image (format)
docker run -d -p <host-port>:<container-port> <image-name>[:<tag>] [-e <varname>=<value>] [--name <container-name>] [-it] [-v <host-dir>:<container-dir>] [--restart unless-stopped]

# -d - means run the container in detached mode
# -p - maps the container port to the host port
# -e - sets the environment variable
# --name - sets the name of the container
# -it - runs the container in interactive mode
# -v - mounts the host directory to the container directory
# --restart unless-stopped - restarts the container (if it stops) unless it is manually stopped
```


