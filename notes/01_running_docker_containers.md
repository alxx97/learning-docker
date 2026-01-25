# Running Docker contaniers


We shall user Docker CLI. Every command starts with `docker` .

1. For launching an image we use:
    
    ```python
    docker run <image-name>
    ```
    
    For example:
    
    ```python
    docker run hello-world
    ```
    
    And the result for this example is:
    
    ```
    Unable to find image 'hello-world:latest' locally
    latest: Pulling from library/hello-world
    198f93fd5094: Pull complete 
    95ce02e4a4f1: Download complete 
    Digest: sha256:05813aedc15fb7b4d732e1be879d3252c1c9c25d885824f6295cab4538cb85cd
    Status: Downloaded newer image for hello-world:latest
    
    Hello from Docker!
    This message shows that your installation appears to be working correctly.
    
    To generate this message, Docker took the following steps:
     1. The Docker client contacted the Docker daemon.
     2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
        (arm64v8)
     3. The Docker daemon created a new container from that image which runs the
        executable that produces the output you are currently reading.
     4. The Docker daemon streamed that output to the Docker client, which sent it
        to your terminal.
    ```
    
    **Important:** If you only use `docker run something` , by default the image will start, but inmediatly it will stop.
    
2. It is possible that the image continues running after starting. For this, we use the flag `-it` after `docker run` .
    
    For example, if we only use:
    
    ```bash
    docker run ubuntu
    ```
    
    Then it will start, but immediatly will stop.
    
    However, if we use:
    
    ```bash
    docker run -it ubuntu
    ```
    
    This will give use an interactive shell in the started container!
    
    ```bash
    ╰─ docker run -it ubuntu
    root@fdbc9b52863b:/# 
    ```
    
    For exit we simply use:
    
    ```bash
    root@fdbc9b52863b:/# exit
    ```
    
3. Adding `-d` will run the container in the background, giving us back control of the shell:
    
    ```bash
    docker run -d <image-name>
    ```
    
    For example:
    
    ```bash
    docker run -d postgres
    ```
    
    This command is very useful for containers for processing data or can be interacted with in some way externally, for example, a container with a DB like PgSQL.
    
    Flag `-d` stands for “detached”.
    
4. For listing containers running in background:
    
    ```bash
    docker ps
    ```
    
    For example, after starting a PgSQL db, you can see something like:
    
    ```bash
    docker ps
    repl@host:/# docker ps
    CONTAINER ID   IMAGE      COMMAND                  CREATED
    4957362b5fb7   postgres   "docker-entrypoint.s..."   About a minute ago
    STATUS              PORTS      NAMES
    Up About a minute   5432/tcp   awesome_curie
    ```
    
5. For stopping a running container we use:
    
    ```bash
    docker stop <container-id>
    ```
    
    or:
    
    ```bash
    docker stop <container-name>
    ```