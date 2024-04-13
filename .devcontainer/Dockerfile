# Use an Ubuntu base image that supports ARM architecture
FROM ubuntu:22.04

# Set the environment variables
ENV DEBIAN_FRONTEND=noninteractive

# Install necessary tools and other dependencies
RUN apt-get update && apt-get install -y \
    curl \
    zsh \ 
    gnupg2 \
    lsb-release \
    build-essential \
    cmake \
    python3-pip \
    && curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | apt-key add - \
    && echo "deb http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" > /etc/apt/sources.list.d/ros2-latest.list \
    && apt-get update \
    && apt-get install -y ros-humble-ros-base \
    && apt-get install -y ros-humble-rmw-cyclonedds-cpp \
    && rm -rf /var/lib/apt/lists/*

RUN sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"

# Install colcon from source
RUN pip3 install -U colcon-common-extensions

# Set Cyclone DDS as RMW Implementation (if using)
RUN echo export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp >> /root/.bashrc

# Source ROS 2 environment and workspace
RUN echo "source /opt/ros/humble/setup.bash" >> /root/.bashrc

# Copy your ROS 2 package into the image
# COPY ./physical /root/physical
ARG WORKSPACE
COPY . ${WORKSPACE}/

WORKDIR ${WORKSPACE}

# Build your ROS 2 package
RUN /bin/bash -c '. /opt/ros/humble/setup.bash && \
    cd /root && \
    colcon build --packages-select physical'

# Set your working directory to the ROS 2 workspace

# Command to run your node
CMD ["zsh"]

