# docker-openssh

This Dockerfile build a container with an openssh service.

## Arguments
This container accept the username and the password of the ssh user as build arguments:
- SSH_USER
- SSH_PASSWORD

## Usage
```
$ docker build -t openssh --build-arg SSH_USER=martin --build-arg SSH_PASSWORD=martinpass docker
$ docker run -d -p 22:22 -v volume_of_another_container:/home/martin/data openssh
$ ssh martin@localhost
```

You can login as martin with martinpass as password. The directory /home/martin/data contains the
files in the volume of your other container.