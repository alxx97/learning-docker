# Variables in Dockerfile

1. For creating a variable in a Dockerfile we use the `ARG` instruction:
    
    ```docker
    ARG <var_name>=<var_value>
    ```
    
    For example:
    
    ```docker
    ARG path=/home/repl
    ```
    
    And for using it on another line, we do it as in bash, using `$<var_name>`. Returning to the previous example:
    
    ```docker
    COPY /local/path $path
    ```
    
    **Important:** This variable can only be used in the Dockerfile and will not be accessible after the image has been built. Furthermore, the variable will not exist in the container when it is launched.
    
    **Some use cases:**
    
    Defining the Python version:
    
    ```docker
    FROM ubuntu
    
    ARG python_version=3.9.7-1+bionic1
    RUN apt-get install python3=$python_version
    RUN apt-get install python3-dev=$python_version
    ```
    
    Setting up a directory:
    
    ```docker
    FROM ubuntu
    ARG project_folder=/projects/pipeline_v3
    
    COPY /local/project/files $project_folder
    COPY /local/project/test_files $project_folder/tests
    ```
    
2. It is possible to specify the values ​​of `ARG` variables in the build statement. To do this, we use the following command:
    
    ```docker
    docker build --build-arg <variable_name>=<variable_value>
    ```
    
    For example, if we have the following Dockerfile:
    
    ```docker
    FROM ubuntu
    ARG project_folder=/projects/pipeline_v3
    
    COPY /local/project/files $project_folder
    COPY /local/project/test_files $project_folder/tests
    ```
    
    We can specify a different value for the `project_folder` variable than the one in the Dockerfile by running the following command:
    
    ```docker
    docker build --build-arg project_folder=/repl/pipeline .
    ```
    
    Finally, the `ARG` variable will be overwritten, and the files will end up in the following paths:
    
    ```docker
    COPY /local/project/files /repl/pipeline
    COPY /local/project/test_files /repl/pipeline/tests
    ```
    
3. It is also possible to define variables using the `ENV` command; the syntax is identical to using `ARG`:
    
    ```docker
    ENV <var_name>=<var_value>
    ```
    
    For example:
    
    ```docker
    ENV DB_USER=pipeline_user
    ```
    
    The difference is that variables defined with the `ENV` instruction will remain accessible after the image has been created; that is, we can use them in the running container as environment variables.

    **Important:** These types of variables cannot be overwritten during building. However, they can be overwritten during container execution using the following command:
    
    ```docker
    docker run --env <key>=<value> <image-name>
    ```
    
    For example, in the official Postgres image there are some environment variables that can be configured when launching the image:
    
    ```docker
    docker run --env POSTGRES_USER=test_db --env POSTGRES_PASSWORD=test_db postgres
    ```
    
    **Important:** Use techniques to keep keys and passwords from being explicitly exposed on the command line or in the instructions executed by Docker when creating or launching an image.
