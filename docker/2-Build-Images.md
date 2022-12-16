# Containerizing an App

This section covers how to build an image for your code. Put in another way, how to containerize an application.

## Sample Dockerfile & Explanation

- Example
  ```Dockerfile
  From alpine
  LABEL maintainer="somebody@gmail.com"
  RUN apk add --update nodejs nodejs-npm
  COPY . /src
  WORKDIR /src
  RUN npm install
  EXPOSE 8080
  ENTRYPOINT ["node", "./app.js"]
  ```

- Explanation
  `WORKDIR` & `ENTRYPOINT` are related. The `./app.js` means using the `app.js` in the `WORKDIR`, which is `/src`.

## Digging Deeper




## Questions
- [ ] When we run the `RUN` command in a `Dockerfile`, do we change directly on the base layer?
- [ ] If the above is true, then why we need multiple layers?
- [ ] If the first question is false, how each layer got combined together and work as a whole image?
  - An fair guess is the `RUN` command layer will record the changes to the file system. The layer will be used in the final image. 

## ToDos
- [X] Read [Best practices for writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
  - [X] Note on the reading
