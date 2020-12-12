# Build our first image

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
RUN apt-get install iputils-ping -y
```

> Pay attention to the `-y` param. Usually, installing software using package manager will prompt user for `Y/n` but there is no interaction during build of image, so commands should skip the prompt.


## Building

Now that we’ve created our Dockerfile, let’s build our image. To do this, we use the `docker build` command.

The docker build command builds Docker images from a Dockerfile and a “context”. A build’s context is the set of files located in the specified `PATH` or `URL`. The Docker build process can access any of the files located in the context. Issuing `docker build` will give an error `"docker build" requires exactly 1 argument.`. This argument is the context, for the Dockerfile it will use the default name `Dockerfile` found.

Let's build using:

```
docker build .
```

## Tagging

Using `docker images` we will notice the newly created image with only id, when other images have names.

```
<none> <none> 1790aa6011b4 'N minutes ago' 101MB
```


The build command optionally takes a `--tag` flag. The tag is used to set the name of the image and an optional tag in the format `‘name:tag’`. We’ll leave off the optional “tag” for now to help simplify things. If you do not pass a tag, Docker will use “latest” as its default tag. You’ll see this in the last line of the build output.

```
docker build --tag ubuntu-ping .
```
