# Lab 4

## Demo Video

[Youtube Link](https://youtu.be/MDMCLlL0XlI)

## Reflection Questions

1. **What are the main differences between a Docker image and a Docker container?**

Docker images are the read-only template or blueprint used to create Docker containers, while Docker containers are the actual lightweight, portable packages of software that are executed. When containers are executed, the Docker daemon uses the Image as the base to create it. Another major difference is that while each container instance from the same Image share the same base layers that make up the Docker Image's architecture, they each have their own unique writable top layer when they are instantiated that allow the user to add new or modify existing data in the container.

2. **Explain how Docker's layered architecture improves efficiency.**

One of the main ways the layered architecture improves efficiency in speed and storage is through its caching system. If a layer in a Docker Image is changed, only that layer and the layers on top of it has to be rebuilt; the layers below are stored in cache. This efficiency is taken further through multi-stage builds in which the base layer is made up of another Image whose layers serve as the foundation for this new Image. This also allows you to condense the size of the Image and its containers even more, since instead of perpetually adding layers to one Image, you can compress layers that are unlikely to be changed into a base Image layer. Furthermore, all containers from the same Image share the Image's layers, only differentiating in the top writable layer; the layers are not duplicated each time a new container is run.

3. **Why does each container get its own writable layer?**

The unique writable layer allows each container to share the same underlying layers that make up the Image that they derive from, making resource usage more efficient since you do not have to rebuild Image layers for every container nor have each container's Image layers individually take up disk space. Furthermore, any changes to the writable layer is isolated to the container without affecting the containers or base image after it is shut down. By extension, it preserves the immutable nature of images ensuring that it remains reproducible and consistent across all environments.

4. **What are the benefits of using Docker Compose over running containers individually?**

Rather than run hundreds or thousands of containers manually each time, you can run them all with their stored parameters written in one YML file. From there, we can interact with each container instance individually as needed, without the pain of individually configuring the parameters for every instance. Furthermore, the YAML files are sharable, which supports collaboration between developers and increases efficiency. Docker Compose also caches configuration needed to create a container which Composes reuses when restarting a service that has not changed; as a result, environment changes are applied rapidly. Finally, Compose supports storing variables in the Compose file, which supports portability across environments as you can take advantage of them to customize for different environments or users.

## Notes
