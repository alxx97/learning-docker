# Working with Docker containers

1. We can customize the container name using the `--name` flag as follows:
    
    ```bash
    docker run --name <container-name> <image-name>
    ```
    
    This will make it easier for us to find out if we ever need to stop the execution.
    
2. To filter running containers:
    
    ```bash
    docker ps -f "name=<container-name>"
    ```
    
    This allows us to show the execution details of the specified container; in fact, it is not necessary to specify the exact name. In this case, the `-f` flag helps us to filter using matches in the container name.
    
3. To review the logs of a running container:
    
    ```bash
    docker logs <container-id>
    ```
    
    or:
    
    ```bash
    docker logs <container-name>
    ```
    
    Also, if we want real-time logs, we can use the `-f` flag:
    
    ```bash
    docker logs -f <container-name>
    ```
    
    **Note:** To exit this log stream, use CTRL+C.
    
4. To remove a container that has already been completely stopped, we use:
    
    ```bash
    docker container rm <container-id>
    ```
    
    or simply:
    
    ```bash
    docker container rm <container-name>
    ```
