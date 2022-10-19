# sub container image
# Start from light-weight ROS container
FROM ros:galactic-ros-core

# Define environment variables
ENV HOME=/root
WORKDIR ${HOME}

# Copy listener binary from development to production container
COPY --from=ros-galactic:dev-env ${HOME}/dev_ws/build/cpp_sub/listener .