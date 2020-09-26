# Django docker and api

## Docker 
 
 Docker is really just Linux containers which are a type of virtualization
 
## Install Docker
 You can check the official website and check whats best for you here  https://www.docker.com/get-started 

> if your using linux you will also need to use this command 
> sudo pip install docker-compose 

## Hello world 
To confirm Docker installed correctly we can run our first command   

```
docker run hello-world

```
This will download an official image and then run the container. We’ll discuss both images and containers shortly.

you should get something like this 

```
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
1b930d010525: Pull complete
Digest: sha256:9572f7cdcee8591948c2963463447a53466950b3fc15a247fcad1917ca215a2f
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

```

A good command to inspect Docker is

```
docker info 
```
Want to inspect just the current image?

```
$ docker image ls

```

## Images and Containers
Images and containers are the two fundamental concepts to grasp when you start with Docker. An image is a snapshot in time of what a project contains. A container is a running instance of the image.

When we ran hello-world we used an official Docker image. We did not have to create the image ourself. But typically we will create custom images and we do so using a Dockerfile. We also will use docker-compose.yml files to run the containers.

A baking analogy we can use here is as follows:

* A Dockerfile is the recipe for a cake
* An image is a snapshot of the recipe at a given time
* A docker-compose.yml says how to make the cake
* And the container is the actual, baked cake


Ok, let’s create our own image 

```
$ cd ~/Desktop
$ mkdir code && cd code
$ mkdir python3.7 && cd python3.7

```
after that create a dockerfile 

```
$ touch Dockerfile

```

With your text editor add the following single line of code to the Dockerfile.

```
# Dockerfile
FROM python:3.7-alpine

```
With our instructions complete it’s time to “build”
```
$ docker image build .

``` 
this should give u something like this 

```
Sending build context to Docker daemon  2.048kB
Step 1/1 : FROM python:3.7-alpine
3.7-alpine: Pulling from library/python
c9b1b535fdd9: Pull complete
2cc5ad85d9ab: Pull complete
53a2fca3c2ea: Pull complete
30fce49de8b1: Pull complete
49bcb9571cc7: Pull complete
Digest: sha256:7655eea15dfd981eeb7d243af21e8561e967709caba938d50b136cdb992f3546
Status: Downloaded newer image for python:3.7-alpine
 ---> b2c276538711
Successfully built b2c276538711

```


## Containers
Now that we have our Python image how do we run it? Well just as a Dockerfile is a list of image instructions there is also a docker-compose.yml file that is a list of container instructions.

> create a basic django project 

# Dockerized Django
inside the basic django project you created 

``` 
touch Dockerfil
touch docker-compose.yml

```

inside the dokerfile fill it with this 
```
# Dockerfile

# Python version
FROM python:3.7-alpine

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Set work directory
WORKDIR /code

# Install dependencies
COPY Pipfile Pipfile.lock /code/
RUN pip install pipenv && pipenv install --system

# Copy project
COPY . /code/

```

inside the docker-compose.yml

```
# docker-compose.yml
version: '3.7'

services:
  web:
    build: .
    command: python /code/manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/code
    ports:
      - 8000:8000

```

now 
```
docker-compose up --build

```
you will see this 

```
Creating network "djangoapp_default" with the default driver
Building webStep 1/6 : FROM python:3.7-alpine
...
Successfully built 047a6d848c5b
Successfully tagged djangoapp_web:latest
Recreating djangoapp_web_1 ... done
Attaching to djangoapp_web_1
web_1  | Performing system checks...
web_1  |
web_1  | Watching for file changes with StatReloader
web_1  | System check identified no issues (0 silenced).
web_1  |
web_1  | You have 17 unapplied migration(s). Your project may not work properly until you apply the migrati
ons for app(s): admin, auth, contenttypes, sessions.
web_1  | Run 'python manage.py migrate' to apply them.
web_1  | January 21, 2020 - 14:49:16
web_1  | Django version 3.0, using settings 'example_project.settings'
web_1  | Starting development server at http://0.0.0.0:8000/
web_1  | Quit the server with CONTROL-C.

```

and thats it 
your done 

