# Running Docker contaniers

We will use Docker CLI. Every command starts with `docker`.

1. For starting an image:
    ```shell
    docker run <image-name>
    ```
    Example:
    ```shell
    docker run hello-world
    ```
    The result is:
    ```
    Unable to find image 'hello-world:latest' locally
    latest: Pulling from library/hello-world
    198f93fd5094: Pull complete 
    95ce02e4a4f1: Download complete 
    Digest: sha256:05813aedc15fb7b4d732e1be879d3252c1c9c25d885824f6295cab4538cb85cd
    Status: Downloaded newer image for hello-world:latest

    Hello from Docker!
    This message shows that your installation appears to be working correctly.
    ```
2. It is possible that the image keeps running after starting. For exmple, if you simply run ubuntu image with the following command:
    ```shell
    docker run ubuntu
    ```
    Then it will start, but immediatly will stop.
    
    However, if you add the flag `-it`, then docker will give us an interactive shell in the started container.
    ```shell
    docker run -it <imagen-name>
    ```

    For example, with the ubuntu image:
    ```shell
     docker run -it ubuntu
    ```
    Give us:
    ```
    ╰─ docker run -it ubuntu
    Unable to find image 'ubuntu:latest' locally
    latest: Pulling from library/ubuntu
    36bf709aa36d: Pull complete 
    3818b7c88702: Download complete 
    Digest: sha256:cd1dba651b3080c3686ecf4e3c4220f026b521fb76978881737d24f200828b2b
    Status: Downloaded newer image for ubuntu:latest
    root@698c3841e14e:/# 
    ```
    That is an interactive shell in the started container!
