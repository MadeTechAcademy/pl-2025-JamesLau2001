# Using docker
There's a basic node app in the docker-app folder.

## Tasks

- Build a docker image using the given dockerfile
. docker build -t docker-revision .
. -t lets us name the container, in this case I named it docker-revision, the '.' tell's it to build the container in the current directory where the dockerfile is
. When you build, you get the ID of the container

- Run the image you have built in a local container (in detached mode)
. docker run -d -p 127.0.0.1:3000:3000 docker-revision
. 127.0.0.1:3000:3000, publishes the local host port 3000 to 127.0.0.1:3000

- Visit the site at http://localhost:3000
- Check the logs of the running app in the container
. docker logs {container ID}

- Stop and remove the container
. docker stop {container ID}
Running checking logs here will show that ELIFECYCLE Command failed showing it's been stopped
. docker rm {container ID}
Running docker logs here will show that the no such container exists, meaning it has been removed

### Notes
Add your thoughts and questions here


## Stretch task
Consider how you might use `docker compose` tools to locally to build, spin up, shut down and clean up containers
. A tool for defining and running multi-container applications
. When applicatios grow in size, the number of operations will increase, for example let's say you now have to connect to a DB, this means that the container then needs to run the script in the codebase, as well as connecting to the DB, this makes the container slow
. By separating these tasks into separate containers, it becomes more efficient

### Record your results
Add your thoughts here and add any files you created into the exercise folder


