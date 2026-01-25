# Changing users and working directory

**Important:** Some Docker instructions can affect the behavior of subsequent instructions.

1. We use the `WORKDIR` command to change the working directory for all the following commands:
    
    ```docker
    WORKDIR /path/del/nuevo/working/directory
    ```
    
    This instruction is very useful for shortening paths in instructions like `COPY`, because it allows us to use relative paths.

    The `WORKDIR` instruction also affects the `RUN` and `CMD` instructions.
    
2. We use the `USER` instruction to change the user in all of the following instructions:
    
    ```docker
    USER my_user
    ```
    
    As we recall, in OS like Linux we can create users and grant each of them permissions, such as access to folders, read, write, execute permissions, etc.
    
    In particular, the root user has all permissions.
    
    **Best practices**
    
    - As a best practice, it's recommended to use the root user to create new users with permissions for specific tasks.

    - It's also recommended not to run all commands as root. When launching a container, for example in Ubuntu, the default user is root.
