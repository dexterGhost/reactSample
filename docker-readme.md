1. Makes like easy for installation of softwares and their related dependencies
2. Docker is an ecosystem containing of client, server, machine, images, hub, compose…. all together responsible for creating an image which can be used for running containers. Image will contain all the dependencies required to run the program(s)
3. Container is an instance of a running program/Container is a program with its own set of hardware resources (own networking tech, own hdd, own memory)
4. Docker commands:
    - docker run <image name> <override command from image (if any)> //run container. ((docker run = docker create + docker start))
    - docker run -d runs process in background
    - docker ps //list running containers
    - docker ps —all //list all created containers
    - docker system prune //stop all processes, delete all cache and processes
    - docker logs //see all logs emitted from the container
    - docker stop <containerId> or docker kill <containerId>. Docker stop takes about 10 seconds to shut down the process nicely (releasing memory and what not). Kill on the other hand is instantaneous
    - docker exec -it <containerId> <command for container> //exec -it helps us to run a command against a running container
    - docker build //used to build our an image from a docker file
    - docker build -t <dockerId>/<project name>:<version/latest> //used to tag a build so we do not have to use the container id each time while running docker image
    - docker run -p //used for port mapping (so incoming requests can go to this port) usage ~ docker run -p 5000:8080 <containerName>
    - docker-compose //used to start up multiple docker containers at the same time and form a networking between them. Can also be used when we have just a single container but complex run command.
        - docker-compose up (equivalent to run) && docker compose run —build (re-build and run)
        - docker-compose up -d (run multiple containers in background)
        - docker-compose down  (stop all containers)
    - Docker volumes are used to setup a mapping between file/folder of docker container and local file system. //used with -v switch
5. By default, containers are completely isolated and do not share anything
