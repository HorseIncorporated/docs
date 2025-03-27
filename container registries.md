# guide

**Using a prebuilt image:**

- Determine the published URL of the prebuilt image you want to use
- Reference it in your `devcontainer.json`, Dockerfile, or Docker Compose file
    - In our previous guide on [“Using Images, Dockerfiles, and Docker Compose,”](https://containers.dev/guide/dockerfile) we also showed how you can use prebuilt images, Dockerfiles, or Docker Compose files for your configurations
- Build your image and push it to a container registry (like the [Azure Container Registry](https://learn.microsoft.com/azure/container-registry/container-registry-get-started-docker-cli?tabs=azure-cli), [GitHub Container Registry](https://docs.github.com/packages/working-with-a-github-packages-registry/working-with-the-container-registry#pushing-container-images), or [Docker Hub](https://docs.docker.com/engine/reference/commandline/push)):
    
    ```
       devcontainer build --workspace-folder . --push true --image-name <my_image_name>:<optional_image_version>
    ```
    
- You can automate pre-building your image by scheduling the build using a DevOps or continuous integration (CI) service like GitHub Actions. We’ve created a [GitHub Action](https://github.com/marketplace/actions/dev-container-build-and-run-action) and [Azure DevOps task](https://marketplace.visualstudio.com/items?itemName=devcontainers.ci) to help with this.
