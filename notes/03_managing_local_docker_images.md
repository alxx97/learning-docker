# Managing local Docker images

Docker Hub is a site where we can find a wide variety of Docker images for various common uses.

1. To download an image from Docker Hub we use:
    
    ```bash
    docker pull <image-name>
    ```
    
    When we download an image, we will always get the latest version available.
    
    We can check the list of image versions on Docker Hub.
    
    For downloading a specific version, we use:
    
    ```bash
    docker pull <iumage-name>:<image-version>
    ```
    
2. To list the images available on our device:
    
    ```bash
    docker images
    ```
    
3. To delete an image from our machine:
    
    ```bash
    docker image rm <image-name>
    ```
    
    **Important:** All containers based on that image must be stopped before be removed.
    
4. To clean all the stopped containers, we can use:
    
    ```bash
    docker container prune
    ```
    
5. To delete all unused images, run:
    
    ```bash
    docker image prune -a
    ```
    
    We use the `-a` flag to remove all unused images. This is very common when we develop our own images and some of them end up without tags or names.