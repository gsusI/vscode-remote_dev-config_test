# Setting a docker-based remote development environment using Visual Studio Code.

We'll be setting a docker-based remote development environment, which will pretty much replace in full your local environment, so a laptop with a fresh installation of Visual Studio Code, an SSH access to a Docker Host, and the appropriate config files; can start developing out-of-the-box.

This how-to hasn't been widely tested, for any questions please refer to the main [documentation](https://code.visualstudio.com/docs/remote/containers).

**Feel free to update this repo with your findings by sending a pull-request.**

### This process has been tested in the following environment:
- Laptop OS: Windows 10 Pro
- Laptop dependencies:
    - [Docker Desktop](https://www.docker.com/products/docker-desktop)
    - [Visual Studio Code 1.39.2](https://code.visualstudio.com)
    - VSCode extensions: [Remote Development](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)
- Server OS: Ubuntu 18.04 LTS
- Server dependencies:
    - [Docker 19.03.04](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
    - [Docker Compose 1.24.1](https://docs.docker.com/compose/install/)




### **Steps to follow:**
#### In your local environment:

1. Install [vscode](https://code.visualstudio.com).
2. Install the [Remote Development](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack) extension in VSCode
3. Install the [Docker Desktop](https://www.docker.com/products/docker-desktop).

#### In your remote server:

4. Install [Docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/).
5. Install [Docker Compose](https://docs.docker.com/compose/install/).

#### In your local environment:

6. Open this repository with your local VSCode, and refrain from clicking Open in Container.
7. Tweak .devcontainer/devcontainer.json appropriately.

```
Note that you have three different options to create your dev docker container (to chose one just uncomment that section in .devcontainer/devcontainer.json, and comment the others):
- **Use a DockerHub image.**
- **Use a Dockerfile.**
- **Use Docker Compose:** If using this option you'll need to adjust all docker-compose*.yml files.

    ##### Notes on performance
    Some times Docker can try to consume too much memory, causing an Out of Memory (OOM) issue, that might cause your server to freeze until the OS kills docker. To avoid this you'll need to limit the resources your docker containers can consume.

    For **Docker Compose** you'll need to use version 2, and include resource limits (version 3 won't work as it requires Docker Swarm): mem_limit.
    For **Dockerfile** and **DockerHub image** user runArgs (commented line included in .devcontainer/devcontainer.json).
```

8. Create an SSH tunnel form your local to your remote environment
Using PowerShell in Windows, it'll look like: ```ssh -NL localhost:23750:/var/run/docker.sock <your_remote_host>```
9. Now, everything is ready, go to VSCode, press ```Ctrl``` + ```Shift``` + ```P``` and hit **Remote-Containers: Open Folder in Container...**


**If everything worked fine your container will now be created, and in a few moments you'll be ready to start developing in your**


