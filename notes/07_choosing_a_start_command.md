# Choosing a start command for your Docker image

It is possible to choose a command that will be executed when a container is launched upon initialization of an image.

1. To execute a startup command on an image, we use the `CMD` instruction:
    
    ```docker
    CMD <shell-command>
    ```
    
    The CMD instruction:
    
    1. It runs when the image starts, that is, when we create a container and launch it.
    2. It is not executed when we create the image.
    3. It adds no weight to the final image.
    4. It does not add any time to the construction.
    5. If there are multiple `CMD` instructions, only the last one will have an effect.
    
    Some typical uses of this command:
    
    1. For launching a script:
        
        ```docker
        CMD python3 my_pipeline.py
        ```
        
    2. Lanchung a database:
        
        ```docker
        CMD postgres
        ```
        
    3. Launch a bash script that runs multiple applications:
        
        ```docker
        CMD start.sh
        ```
        
A very important question: when will the container stop running when using `CMD`? This depends on the application being launched.

For example, if it's a Python script with "final", it will stop when the script finishes executing.

If we have a database, the container will stop when we exit the database.

If we launch an Ubuntu image, it will stop when the shell closes with the `exit` command.


## Overwriting the start command

It is possible to override the initial default command; to do this we use:

```docker
docker run <image> <shell-command>
```
