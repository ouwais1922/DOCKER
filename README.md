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

docker run -dit ubuntu


