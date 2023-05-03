![Docker-Logo](https://user-images.githubusercontent.com/72993155/235827494-564e6e6b-d448-4b8b-8d8d-30f7594029b0.png)

VMs & containers:

1- Architecture: Containers share the same  operating system kernel, whereas VMs require a separate operating system instance for each VM. This means that containers are more lightweight and use fewer resources compared to VMs, which need to replicate the entire operating system.

2- Isolation: Containers provide a level of isolation between applications and the host system, but they do not provide the same level of isolation as VMs, which have a complete operating system instance. This can be a security consideration in certain scenarios.

Images & Containers:

Image:
- An image is essentially a snapshot of a Docker container at a specific point in time. 
- Images are used to create containers, which are the running instances of those images.
- Images are read only, if you want to change something, you have to create a new image.

    * App code
    * Any dependecies
    * env variables

Container: (process)
- container is a lightweight and standalone package of software that includes everything needed to run an application, such as code, libraries, system tools, and settings.
- Lightweight
- Portable
- Isolated
- Running instance of an image

RUN IMAGE ==> MAKE A CONTAINER ==> MAKE THE APPLICATION

Image:
Images are made up from several "layers":

- Parent image: includes the OS & the runtime env
- Then we can have anything dependecies, source code ...

## Docker file:

* FROM node:17-alpine : This instruction specifies the base image (parent layer) to use for the Docker image. In this case, it is the official Node.js 17 image, which is based on the Alpine Linux distribution. The Alpine version is a lightweight distribution of Linux, which means that the resulting Docker image will be relatively small.

* WORKDIR /app : sets the working directory to /app
* COPY . .:  This instruction copies all the files from the current directory (the directory containing the Dockerfile) into the /app directory in the Docker image. The first dot (.) refers to the current directory on the host machine, while the second dot refers to the current directory in the Docker image.

* RUN npm install: This instruction runs the npm install command inside the Docker image. This command installs all the dependencies listed in the package.json file for the Node.js application in the /app directory.

* EXPOSE 4000 : This instruction specifies that the Docker container will listen on port 4000 at runtime. It does not actually publish the port or make it accessible from outside the container, but it is a hint to the user running the container that they should map the container port to a port on the host machine when starting the container.

* CMD ["node", "app.js"] : This instruction specifies the default command to run when the Docker container starts. In this case, it runs the Node.js application in the /app directory using the node command and the app.js file as the entry point.

## Command lines:

docker run -dit ubuntu


$ docker build -t my _app .

    - build: This subcommand is used to build an image from a Dockerfile.
    - -t option is -t <name:tag>, where <name> is the name of the image, and <tag> is an optional tag. If no tag is specified, Docker will use the default latest tag.
    - my_app: This is the name of the image that will be created.
    - .: This is the build context, which specifies the directory containing the Dockerfile and any other files needed for the build.

$ docker ps : list runing containers

$ dokcer ps -a : list all containers running, and stopped ones

$ docker stop container_name

$ docker start container_name

$ docker run --name name_container -p 4000:4000 -d image_name

