# Dockerfiles

To simulate user environments copy and modify the Dockerfile in
example-user-templates to match the user's system.

Build the Docker image with the command
`cd /path/containing/dockerfile`
`docker image build -t IMAGE_NAME .`

Run a container from that image in an interactive terminal session with
`docker run -it IMAGE_NAME`

Exit and close the container with
`exit`

Find the container id or name for your old containers with 
`docker ps -a`

Start and return to a previous container session with
`docker start CONTAINER_ID`
`docker attach CONTAINER_ID`

Remove old containers with
`docker rm CONTAINER_ID`
