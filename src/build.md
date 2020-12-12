# Build out first image

In this chapter, we will start building our first image and familisiarize. The completed example is accessible [here](https://github.com/dockerforfriends/webinar-material/blob/main/chapter-4/Dockerfile)

## Dockerfile

A `Dockerfile` is a text document that contains all the commands a user could call on the command line to assemble an image. When we tell Docker to build our image by executing the `docker build` command, Docker reads these instructions and executes them one by one and creates a Docker image as a result.

> The name of the Dockerfile is not important but the default filename for many commands is simply `Dockerfile`. So, we’ll use that as our filename throughout this series.

Here is the format of the Dockerfile:

```
# Comment
INSTRUCTION arguments
```

The instruction is not case-sensitive. However, convention is for them to be UPPERCASE to distinguish them from arguments more easily.

## Base image

Create a directory and create a file named `Dockerfile` and open this file in your text editor.

The first thing we need to do is to add a line in our `Dockerfile` that tells Docker what base image we would like to use for our application. Therefore, instead of creating our own base image, we’ll use the official `ubuntu` image.

```
FROM ubuntu
```

The above is equivalent to 

```
FROM ubuntu:latest
```

## Extending the base image ubuntu

Following we will, update the ubuntu package manager in order to install the `ping` command.

This is done with the `RUN <command>` syntact in the our Dockerfile.

```
RUN apt-get update
RUN apt-get install ping -y
```

> Pay attention to the `-y` param. Usually, installing software using package manager will prompt user for `Y/n` but there is no interaction during build of image, so commands should skip the prompt.


