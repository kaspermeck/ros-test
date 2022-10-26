# sub container image
# Start from light-weight ROS container
FROM ros:galactic-ros-core

# Define environment variables
ENV HOME=/root
WORKDIR ${HOME}

# Copy listener package from development to production container
RUN mkdir ${HOME}/cpp_sub
COPY --from=ros-galactic:dev-env ${HOME}/dev_ws/install/cpp_sub cpp_sub