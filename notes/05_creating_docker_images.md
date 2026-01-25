# Creating your Docker images

- Docker images are blueprints for creating containers.
- For creating these blueprints, we must declare a list of instructions in a text file called a Dockerfile.
- A **Dockerfile** is a text file that contains all the commands that will be executed with the command-line interface (CLI) to install the necessary software, with the understanding that we must use Docker-specific syntax.

## Estructura de un Dockerfile

1. We start by using the keyword `FROM` followed by the base image:
    
    ```docker
    FROM <imagen-base>:<version>
    ```
    
    For example:
    
    ```docker
    FROM ubuntu:latest
    ```
    
2. For creating an image from a Dockerfile, we run:
    
    ```bash
    docker build /path/to/Dockerfile
    ```
    
    If the `Dockerfile` is located in our working directory, we simply run:
    
    ```bash
    docker build .
    ```
    
    If we want to assign a tag to the created image, we include the `-t` flag:
    
    ```bash
    docker build -t my_image .
    ```
    
3. For the execution of a command during image creation, we will use `RUN`, this will be very useful for installing  and packages in our container:
    
    ```bash
    RUN <valid-shell-command>
    ```
    
    For example, if we are using the Ubuntu image:
    
    ```docker
    FROM ubuntu:latest
    
    RUN apt-get update
    RUN apt-get install -y python3
    ```
    
    In the last instruction, we used the `-y` flag because some commands require user input, in this case `y`. Since this isn't possible manually while creating the image, it's necessary to include this flag.
