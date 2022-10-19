1. Build, run and test development environment
  # Change to the development directory
  ros-compose$ cd development/
  
  # Build the development container
  ros-compose/development$ docker compose build
  
  # Run the dev-env service
  ros-compose/development$ docker compose run dev-env

  # (dev-env) Optional step: test colcon and ros2
  dev_ws$ colcon --help
  dev_ws$ ros2 --help
  
  # (dev-env) Start publish and subscribe demo
  dev_ws$ ros2 launch ../ros-compose/launch_files/pub_sub_launch.yml

2. Build, run and test production environment
  # Change to the production directory
  ros-compose$ cd production/
  
  # Build the production containers
  ros-compose/production$ docker compose build
  
  # Run the prod-env-pub and prod-env-sub services
  ros-compose/production$ docker compose up
