# ROS 2 Humble Dev Container (Pop!_OS 24.04)

A clean, reproducible Docker & VS Code Dev Container setup for running **ROS 2 Humble** on **Pop!_OS 24.04** (or Ubuntu 24.04) without touching host OS dependencies or setting up an extra dual-boot.

## Why This Exists

ROS 2 Humble officially targets **Ubuntu 22.04**, while my daily workstation runs **Pop!_OS 24.04**. Instead of risking broken system dependencies or running a heavy VM, this template isolates the entire ROS 2 Humble toolchain inside a lightweight Docker container attached directly to VS Code.

## Architecture

![ROS 2 Humble Docker Architecture](assets/architecture.jpeg)

## Prerequisites

- **Linux Host** (tested on Pop!_OS 24.04)
- **Docker** & **Docker Compose**
- **Visual Studio Code** with the [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension

## Quick Start

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/M7md-salah/ros2-humble-devcontainer.git](https://github.com/M7md-salah/ros2-humble-devcontainer.git)
   cd ros2-humble-devcontainer
   ```

2. **Open in VS Code:**
   ```bash
   code .
   ```
   When prompted in the bottom-right corner, click **Reopen in Container** (or open the Command Palette with `Ctrl+Shift+P` and run `Dev Containers: Reopen in Container`).

3. **Verify the ROS 2 environment inside the container terminal:**
   ```bash
   printenv ROS_DISTRO
   # Expected output: humble
   ```

## Workspace Structure

```text
ros2-humble-devcontainer/
├── .devcontainer/
│   ├── devcontainer.json   # VS Code Dev Container & extensions config
│   └── Dockerfile          # osrf/ros:humble-desktop + auto-sourcing
├── assets/
│   └── architecture.jpeg    # Environment architecture diagram
├── src/                    # Place your ROS 2 packages here
├── docker-compose.yml      # Container orchestration & volume mounts
└── .gitignore              # Ignores colcon build/install/log folders
```

## Roadmap

- [x] Isolated Ubuntu 22.04 + ROS 2 Humble container with VS Code integration
- [x] Automatic ROS 2 environment sourcing on shell startup
- [ ] Enable X11 forwarding & NVIDIA GPU passthrough for RViz2 and Gazebo
- [ ] Add sample C++ (`rclcpp`) Publisher/Subscriber package in `src/`
