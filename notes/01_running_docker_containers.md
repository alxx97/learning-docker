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
    
    ```
    docker run ubuntu
    ```
    
    Then it will start, but immediatly will stop.
    
    However, if we use:
    
    ```
    docker run -it ubuntu
    ```
    
    This will give use an interactive shell in the started container!