# Working with Images 

## Images in Detail

- Overview
  An image is composed by several layers. When you pull images from a registry (docker hub), you can that the pulling is layer by layer. **Layers are put together using `image manifest`.**

- Image pulling
  - Step 1: Get manifest
    - Get `fat manifest` based on your system architecture. E.g.: x86 or arm.
        - Command to get the architecture: `docker system info`
    - Get `image manifest`.
  - Step 2: Pull layers
    - Based on the image manifest, layers will be pulled.
  - Command: `docker image pull <image-name:TAG>`
    - E.g.: `docker pull mcr.microsoft.com/dotnet/aspnet:7.0`
  - **Image are pulled based on the hash value, which helps to get the correct image.**

- Inspecting the image you pulled
  - Find the root folder
    With command `docker system info`, you will see the `Sotrage Driver: overlay2`. The root folder path in Linux is `/var/lib/docker/overlay2/<some-id>/diff`
  - **Layers**
    - Base layers
      - The OS runs in the container that runs the image.
    - App code 
      - E.g.: Redis
  - Find which one is the base layer in the path `/var/lib/docker/overlay2/<some-id>/diff`
    - Unfortunately, the folders in the above path cannot tell which image layer it is. If you want to find a specific layer, such as the base layer, you have to check folder by folder.

- Copy on write
  All the layers are read-only layers in an image. Whenever a container want to change a specific layer, the layer will be copied to the container R/W area and make changes in the copied layer.

- Common commands
  - Pull: `d image pull <image-name:TAG>`
  - List: `d image list`
  - Remove: `d image rm`

## Registry
Whenever we pull images, we are pulling from a registry. For example, the dockerhub or Azure Container Registry. When we pulling an image, we can also say we are pulling to the image to the local registry. **Local registry path is `/var/lib/docker/overlay2`.**

- Pulling command detail
  - Complete Sample: `d image pull docker.io/redis:latest`
  - Part 1: Registry is `docker.io` (Default registry)
  - Part 2: Repo is `redis`
  - Part 3: Image or tag is: `latest` (Default image tag)
  - Another comple sample: `d image pull mcr.microsoft.com/dotnet/aspnet:7.0`

- Push an image to a registry
  - Hash revisit
    The layer id is a hash value, which is content hash. 
  - Stuff to push to registry
    - Image manifest
    - Layers (Compressed)
      - :warning: When we compress the layers, the content changed and original hash value is no longer correct. When we push to a registry, there will be a conflict between the layer ids in the manifest file and the real layer ids.
      - :point_right: Populate the manifest with the new hashes of the compressed layers.

- Caveats
  - Latest tag
    - The `latest` tag of an image doesn't mean it is REALLY the latest. It means the latest stable image. There could be `edge` images, which are the latest but not stable.
  - Official images
    - [Docker Official Images](https://docs.docker.com/docker-hub/official_images/)


## ToDo
- [ ] Create an image with `latest` and `edge` images.
- [ ] Find a concrete example on the layer `copy on write` operation.
- [X] How to distinguish official images and unofficial images.
    - In [DokerHub](https://hub.docker.com/search?q=), official will have tag `DOCKER OFFICIAL IMAGE`.






