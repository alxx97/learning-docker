# Distributing Docker images

You can share images you've created in two ways:

- Sharing the images as files
- Using a Docker Registry server

1. For downloading an image from a private container registry:

```bash
docker pull link-to-private-registry.com/my_image:v1
```

2. To uploading an image to a registry:
    
    ```bash
    docker image push <image-name>
    ```
    
    For uploading an image to a specific container registry, we must first ensure that the image name begins with the registry name. This can be done using the following command:
    
    ```bash
    docker tag my-image:v1 link-to-my-registry.com/my-image:v1
    ```
    
    Then we upload the image to the registry:
    
    ```bash
    docker image push link-to-my-registry.com/my-image:v1
    ```
    
2. If you use private registries, you need to authenticate. To do this, you can use:
    
    ```bash
    docker login link-to-private-registry.com
    ```
    Then it will ask for our credentials.
    
3. For saving an image as a file, we use:
    
    ```bash
    docker save -o image.tar my-image:v1
    ```
    
4. For loading an image from a file, we use:
    
    ```bash
    docker load -i image.tar
    ```
