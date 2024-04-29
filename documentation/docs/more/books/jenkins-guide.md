jenkins

1.  Adding Restart Policies:

    You might want to add a restart policy to ensure that the Jenkins container automatically restarts if it crashes or if Docker restarts. This can be done using the `--restart` flag. For example, you could use `--restart` unless-stopped to ensure the container restarts unless explicitly stopped.

2.  Volume Mounts for Persistence:

    Jenkins typically stores its data in `/var/jenkins_home` directory within the container. If you want to persist Jenkins data between container restarts or updates, you can mount a volume from the host machine to this directory. This can be achieved using the `-v` flag. For example, `-v` `jenkins_home:/var/jenkins_home` would mount a volume named `jenkins_home` to the Jenkins home directory.


```bash title="bash"
docker run -d \
  -p 8080:8080 \
  -p 50000:50000 \
  --name jenkins \
  --restart unless-stopped \
  -v jenkins_home:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkins/jenkins:lts
```

This command ensures that the Jenkins container runs in detached mode, exposes ports `8080` and `50000`, has a restart policy set to "unless stopped," mounts a volume named `jenkins_home` for data persistence, and uses the LTS version of the Jenkins image.

> Notes:

The `-v` flag in Docker is used to specify volume mounts. It allows you to create a persistent data volume outside the container and mount it into the container at a specified path.

For example, `-v` `/host/directory:/container/directory` would mount the directory `/host/`directory on the host machine into the directory `/container/directory` within the container.

In the context of running Jenkins, you typically want to persist Jenkins data, such as configuration, plugins, and job data, across container restarts. This is achieved by mounting a volume to the `/var/jenkins_home` directory within the Jenkins container.

So, when you use `-v` `jenkins_home:/var/jenkins_home`, Docker will create a volume named jenkins_home and mount it into the `/var/jenkins_home` directory in the container. This ensures that Jenkins data is stored outside the container and persists even if the container is removed or recreated.

In summary, when you see `-v` in a Docker command, it's indicating a volume mount, allowing you to persist data outside the container.

---


## Docker with Docker-in-Docker (DinD): 

If you're running Jenkins within a Docker container, you can use Docker-in-Docker (DinD) to allow Jenkins to run Docker commands inside its own Docker containers. However, this approach has security implications and might not be recommended for production use without proper precautions.


```bash title="bash"
docker run -d \
  -p 8080:8080 \
  -p 50000:50000 \
  --name jenkins \
  --restart unless-stopped \
  -v jenkins_home:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkins/jenkins:lts
```

If you want to include Docker-in-Docker (DinD) functionality in your Jenkins container setup, you'll need to bind the Docker socket (/var/run/docker.sock) from the host machine to the Jenkins container. This allows the Jenkins container to communicate with the Docker daemon running on the host machine.

Here's the modified command to include the Docker socket binding:

```bash title="bash"
docker run -d \
  -p 8080:8080 \
  -p 50000:50000 \
  --name jenkins \
  --restart unless-stopped \
  -v jenkins_home:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkins/jenkins:lts
```

I've added `-v` `/var/run/docker.sock:/var/run/docker.sock` to the command, which binds the Docker socket from the host to the Jenkins container. This allows Jenkins to execute Docker commands inside the container.

Now, with this setup, your Jenkins container will have access to Docker commands, allowing you to run Docker builds, start containers, and manage images as part of your Jenkins jobs or pipeline. Make sure to consider the security implications of allowing Jenkins to access the Docker daemon in this way.


---

{==
Solving
==}

If you want to pull Docker images within your Jenkins Dockerfile without adding the Docker installation steps, you can indeed simplify your Dockerfile. Here's how you can modify it to only pull Docker images:

```bash title="bash"
FROM jenkins/jenkins:lts

USER root

# Add Jenkins user to Docker group
RUN usermod -aG docker jenkins

USER jenkins
```

With this Dockerfile, you're starting from the official Jenkins LTS image, switching to the root user to add the Jenkins user to the Docker group, and then switching back to the Jenkins user. This will allow Jenkins to pull Docker images without needing to install Docker within the Jenkins container itself.

Remember that for this to work, you'll still need to mount the Docker socket from the host machine into the Jenkins container when you run the container. This will allow Jenkins to communicate with the Docker daemon running on the host and pull Docker images. Here's an example of how you can run the container with the Docker socket mounted:


```bash title="bash"
docker run -d \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -p 8080:8080 \
  -p 50000:50000 \
  --name jenkins \
  your_custom_jenkins_image
```

Replace `your_custom_jenkins_image` with the name of your custom Jenkins image built from the Dockerfile. With this setup, your Jenkins container will be able to pull Docker images using the Docker CLI on the host machine.

---

## Docker Images Types

In Docker, an `image` is a lightweight, standalone, and executable package that includes everything needed to run a piece of software, including the code, a runtime, libraries, environment variables, and configuration files. When you run a Docker image, it creates a container, which is an instance of that image.

Whether an image "runs" or not depends on what it's designed to do:

1.  **Runnable** Images:

    These are images designed to start a process or service that runs continuously or performs some action until explicitly stopped. Examples include web servers, databases, or any other application that provides a service and needs to keep running.


2.  **One-shot** Images:

    Some images are designed to perform a specific task or action and then exit. These images are typically used for utilities, scripts, or diagnostic tools. They execute their task and then terminate. The `hello-world` image is an example of this. Other examples might include images for performing backups, data migrations, or other batch operations.

So, all images can be run, but the behavior of what they do when they're run can differ. Some images are meant to continuously run services, while others perform a task and then exit.

> Notes:

Containers need a runnable image to exist. 

## [Types of Containers in Docker](https://www.shiksha.com/online-courses/articles/different-types-of-docker-containers/)

- **Stateless** Containers
- **Stateful** Containers
- **Ephemeral** Containers

---

## Dockerfile application

To create a simple HTML file with "Hello, World!" content and then build a Docker image containing this HTML file, you can follow these steps:

1.  Create a simple HTML file named index.html with the "Hello, World!" content:

    ```html title="html"
    <!-- index.html -->
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Hello, World!</title>
    </head>
    <body>
        <h1>Hello, World!</h1>
    </body>
    </html>
    ```

2.  Create a `Dockerfile` in the same directory to build the Docker image:

    ```
    # Dockerfile
    FROM nginx:alpine
    COPY index.html /usr/share/nginx/html/index.html
    ```

3.  Now, build the Docker image using the docker build command:

    ```sh title="bash"
    docker build -t hello-world-html .
    ```

    This command builds a Docker image named `hello-world-html` using the Dockerfile in the current directory (`.`).

4.  Once the image is built, you can run a container from it:

    ```sh title="bash"
    docker run -d -p 8080:80 --name hello-world-container hello-world-html
    ```

    This command runs a container from the `hello-world-html` image, maps port `8080` on the host to port 80 in the container (`-p 8080:80`), and gives the container a name (`--name hello-world-container`).

    Now, you can visit `http://localhost:8080` in your web browser to see the "`Hello, World!`" message served by the Docker container running the HTML file.

That's it! You've created a simple HTML file, built a Docker image containing it, and run a Docker container serving the HTML content.

---

## Pushing `images` to `Dockerhub`

To push your Docker image to Docker Hub (which is commonly referred to as Docker's public registry), you need to follow these steps:

-   **Tag your image:**

    Before pushing your image, you need to tag it with your Docker Hub username and the repository name. The format is `username/repository:tag`. If you haven't tagged your image yet, you can do it using the following command:

    ```sh title="bash"
    docker tag hello-world-html yourusername/hello-world-html:latest
    ```

    Replace `hello-world-html` with the name of your local image, and `yourusername` with your Docker Hub username. You can choose any tag you want; `latest` is commonly used.

-   **Log in to Docker Hub:**

    Use the docker login command to log in to your Docker Hub account.

    ```sh title="bash"
    docker login
    ```

    Enter your Docker Hub username and password when prompted.

-   **Push your image:**

    After logging in, you can push your image to Docker Hub using the docker push command:

    ```sh title="bash"
    docker push yourusername/hello-world-html:latest
    ```

    Replace `yourusername/hello-world-html:latest` with the full name of your image, including the tag you used.

-   **Verify:**

    Once the push is complete, you can go to your Docker Hub account in your web browser to verify that the image has been successfully pushed.

Your image is now available on Docker Hub and can be pulled by anyone with access to it. Remember that if you plan to share your image publicly, make sure not to include any sensitive information or credentials within the image.

---

## Reference

- [What is a Docker image?](https://www.techtarget.com/searchitoperations/definition/Docker-image)

- [Different Types of Docker Containers](https://www.shiksha.com/online-courses/articles/different-types-of-docker-containers/)

- [Docker images](https://www.geeksforgeeks.org/what-is-docker-image/)