# Use an Ubuntu base image that supports ARM architecture
FROM ubuntu:22.04

# Set the environment variables
ENV DEBIAN_FRONTEND=noninteractive

# Install necessary tools and other dependencies
RUN apt-get update && apt-get install -y \
    curl \
    gnupg2 \
    lsb-release \
    build-essential \
    cmake \
    python3-pip \
    && curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | apt-key add - \
    && sh -c 'echo "deb [arch=arm64] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" > /etc/apt/sources.list.d/ros2-latest.list' \
    && apt-get update \
    && apt-get install -y ros-humble-ros-base \
    && rm -rf /var/lib/apt/lists/*

# Install colcon from source
RUN pip3 install -U colcon-common-extensions

# Set Cyclone DDS as RMW Implementation (if using)
RUN echo export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp >> /root/.bashrc

# Source ROS 2 environment and workspace
RUN echo "source /opt/ros/humble/setup.bash" >> /root/.bashrc

# Set your working directory
WORKDIR /your_workspace
    