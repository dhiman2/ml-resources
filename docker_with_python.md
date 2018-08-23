# Using docker with python

`docker run ubuntu /bin/echo 'Hello world'`

`docker run -it --rm ubuntu /bin/bash`

* `--rm` flag automatically removes the container when the process exits. By default, containers are not deleted. This container exists until we keep the shell session and terminates when we exit the session (like an SSH session with a remote server).

If you want to keep the container running after the end of the session, you need to daemonize it:

`docker run --name daemon -d ubuntu /bin/sh -c "while true; do echo hello world; sleep 1; done"`

* `--name daemon` assigns daemon name to a new container. If you don’t specify a name explicitly, Docker will generate and assign it automatically.
* `-d` flag runs the container in the background (i.e., daemonizes it).

`docker ps -a`

Let’s check the logs and see what the daemon container is doing right now:

`docker logs -f daemon`

* `docker logs` fetch the logs of a container.
* `-f` flag to follow the log output.

Now let’s stop the daemon container:

`docker stop daemon`
`docker ps -a`

Now, stop it again and remove all the containers manually:

`docker stop daemon`
`docker rm first_container_name`
`docker rm daemon`

To remove all containers, we can use the following command:

`docker rm -f $(docker ps -aq)`
