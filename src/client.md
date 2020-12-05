# Docker client

Let's see in practice what we have learned so far by familiarizing our selfs with the Docker client interface.

First of all, start your Docker daemon or else `docker` commands may result in following error:

```
Error response from daemon: dial unix docker.raw.sock: connect: connection refused
```

# Containers

We learned that containers are running processes that Docker daemon (`dockerd`) manages. We can list the container with `docker ps`

> Try it!

So, no container currently running. We will require an image to use in order to get a container running.

# Images

In order to list all local images we can issue `docker images`.

> Try it!

No images or nothing interesting, lets go to [Docker hub](https://hub.docker.com) to find an image. Found this [hello-world](https://hub.docker.com/_/hello-world) image so let's use this to play around.

In order to make this image available to run we should instruct our Docker dameon to pull it with:

```
docker pull hello-world
```

> Try it!

Which results in:

```
$ docker pull hello-world
Using default tag: latest
latest: Pulling from library/hello-world
0e03bdcc26d7: Pull complete
Digest: sha256:e7c70bb24b462baa86c102610182e3efcb12a04854e8c582838d92970a09f323
Status: Downloaded newer image for hello-world:latest
docker.io/library/hello-world:latest
```

Let's see what `docker images` will list now.

> Try it!

```
$ docker images
REPOSITORY                   TAG                               IMAGE ID            CREATED             SIZE
hello-world                  latest                            bf756fb1ae65        11 months ago       13.3kB
```

# Running my first container

In order to run our first container we should `docker run {image}` with the name of the image previously pulled from registyre, like:

```
docker run hello-world
```

> Try it!

Now, let's see where our container with `docker ps`.

> Try it! 

Nothing to see, **but why?** There is nothing to see because the hello-world program done all his work and exited. We can list all exited containers with `--all` option, like:

```
docker ps --all
```
> Try it!

This should result in:
```
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES
9410dfc4526a        hello-world         "/hello"            6 minutes ago       Exited (0) 6 minutes ago                       romantic_kare
```

Before closing, what would you say to run something _more ambitious_ like `docker run -it ubuntu bash`.

> Try it!

In a nutshell:
- Docker client instruct Docker daemon to run a container with an image called `ubuntu`.
- Docker dameon will try to pull if he does not have the image available locally.
- The option `-it` will make it available to have an interactive pseudo-TTY with the container.
- The `bash` would be the application that will be executed in the container and this would allow us to look around inside.
