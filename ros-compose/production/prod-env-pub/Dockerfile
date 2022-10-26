# pub container image
# Start from light-weight ROS container
FROM ros:galactic-ros-core

# Define environment variables
ENV HOME=/root
WORKDIR ${HOME}

# Copy talker package from development to production container
RUN mkdir ${HOME}/cpp_pub
COPY --from=ros-galactic:dev-env ${HOME}/dev_ws/install/cpp_pub cpp_pub/