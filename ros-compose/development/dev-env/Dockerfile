# Dockerfile inspired by 
# -- https://docs.ros.org/en/galactic/Tutorials/Workspace/Creating-A-Workspace.html
# -- https://docs.ros.org/en/galactic/Tutorials/Writing-A-Simple-Cpp-Publisher-And-Subscriber.html
# -- https://docs.docker.com/develop/develop-images/multistage-build/
# -- https://docs.docker.com/compose/

FROM ros:galactic-ros-base-focal

# Prepare env
ENV HOME=/root
RUN mkdir -p ${HOME}/dev_ws/src

# Create pub and sub ROS package
WORKDIR ${HOME}/dev_ws/src
RUN . /opt/ros/galactic/setup.sh && \
    ros2 pkg create --build-type ament_cmake cpp_pub && \
    ros2 pkg create --build-type ament_cmake cpp_sub

# Add dependencies for cpp_pub package, in packages.xml and CMakeLists.txt
WORKDIR ${HOME}/dev_ws/src/cpp_pub
RUN sed -i '/<buildtool_depend>ament_cmake<\/buildtool_depend>/a \ \ <depend>rclcpp<\/depend>\n\ \ <depend>std_msgs<\/depend>' package.xml
RUN sed -i '/find_package(ament_cmake REQUIRED)/a find_package(rclcpp REQUIRED)\nfind_package(std_msgs REQUIRED)' CMakeLists.txt
RUN sed -i '/ament_package()/i add_executable(talker src\/publisher_member_function.cpp)\nament_target_dependencies(talker rclcpp std_msgs)\n\ninstall(TARGETS\n\ \ talker\n\ \ DESTINATION lib\/${PROJECT_NAME})\n' CMakeLists.txt

# Add dependencies for cpp_sub package, in packages.xml and CMakeLists.txt
WORKDIR ${HOME}/dev_ws/src/cpp_sub
RUN sed -i '/<buildtool_depend>ament_cmake<\/buildtool_depend>/a \ \ <depend>rclcpp<\/depend>\n\ \ <depend>std_msgs<\/depend>' package.xml
RUN sed -i '/find_package(ament_cmake REQUIRED)/a find_package(rclcpp REQUIRED)\nfind_package(std_msgs REQUIRED)' CMakeLists.txt
RUN sed -i '/ament_package()/i add_executable(listener src\/subscriber_member_function.cpp)\nament_target_dependencies(listener rclcpp std_msgs)\n\ninstall(TARGETS\n\ \ listener\n\ \ DESTINATION lib\/${PROJECT_NAME})\n' CMakeLists.txt

# Copy source code from host src folder to container
COPY ./src/publisher_member_function.cpp ${HOME}/dev_ws/src/cpp_pub/src
COPY ./src/subscriber_member_function.cpp ${HOME}/dev_ws/src/cpp_sub/src

# Compile cpp_pub and cpp_sub ROS packages which contain publisher and subscriber functions
WORKDIR ${HOME}/dev_ws
RUN . /opt/ros/galactic/setup.sh && \
    rosdep install -i --from-path src --rosdistro galactic -y && \
    colcon build --packages-select cpp_pub cpp_sub

# Setup environment
RUN echo "source ${HOME}/dev_ws/install/setup.bash" >> ${HOME}/.bashrc