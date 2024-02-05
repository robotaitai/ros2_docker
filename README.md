# ROS 2 Docker Development Environment

This repository contains a Docker-based development environment for ROS 2 projects. It's designed to provide a standardized setup for working with ROS 2 across different machines and platforms, ensuring compatibility and ease of use.

## Features

- Ubuntu 22.04 base image with support for both x86_64 and ARM64 architectures.
- Pre-installed ROS 2 Humble Hawksbill distribution.
- Additional ROS 2 development tools and dependencies, including `colcon` and custom ROS 2 messages support.
- Integrated VS Code development environment setup via `.devcontainer`.

## Prerequisites

- [Docker](https://www.docker.com/)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Remote - Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) for VS Code

## Getting Started

1. **Clone the repository**:
```
git clone https://github.com/robotaitai/ros2_docker.git
```


2. **Open the project in Visual Studio Code**:
- Launch VS Code.
- Navigate to `File > Open Folder...` and select the cloned `ros2_docker` directory.
3. **Reopen in a Container**:
- A prompt may appear in the bottom right asking to reopen in a container. Click `Reopen in Container`.
- Alternatively, open the Command Palette (`Ctrl+Shift+P`), and type `Remote-Containers: Reopen in Container`.

## Building the Docker Image

- The Docker image can be built manually using:
```
cd ros2_docker/.devcontainer
docker build -t ros2_docker_dev .
```


## Using the Development Environment

- Once the container is running, you can use the integrated terminal in VS Code to interact with the ROS 2 environment.
- To create a new ROS 2 package or work with existing ones, navigate to the `src` directory in your workspace.

## Customizing the Docker Environment

- You can customize the Docker environment by modifying the `Dockerfile` or the `.devcontainer/devcontainer.json` configuration according to your project needs.

## Contributing

Contributions to improve the development environment or to add new features are welcome. Please submit a pull request or open an issue for discussion.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
