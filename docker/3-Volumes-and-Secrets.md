# Volumes and Secrets

## Volumes

- Command to test
  ```bash
  docker container run -dit --name voltest \
  --mount source=ubervol,target=/vol alpine:latest
  ```
  :warning: The `,` between `source=ubervol,target=/vol` is needed. Also, this is the most important part `--mount source=ubervol,target=/vol`.

- :exclamation: Here are some points on docker volumes:
  - If the volume doesn't exist, the above command will create the docker volume.
  - The created docker volumes can be found in path `/var/lib/docker/volumes`.
  - Data you put into the docker volume through certain container can be found in path `/var/lib/docker/volumes/_data`.
  - Use command to log into the container `docker exec -it <container-name> <program-name>`.
    - Example: `docker exec -it voltext sh`
  - Use command to delete the container `docker container rm voltest -f`

## Secrets



