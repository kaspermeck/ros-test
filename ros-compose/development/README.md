# Docker Compose to Build Development Environment Container

Compile container
```
ros-test/ros-compose/development$ docker compose build
```

Run the dev-env container interactively
```
ros-test/ros-compose/development$ docker compose run dev-env
```

Launch talker applications inside the container
```
~/dev_ws# ./install/cpp_pub/lib/cpp_pub/talker 
[INFO] [1666147046.545890132] [minimal_publisher]: Publishing: 'Hello, world! 0'
[INFO] [1666147048.545855103] [minimal_publisher]: Publishing: 'Hello, world! 1'
[INFO] [1666147050.545963454] [minimal_publisher]: Publishing: 'Hello, world! 2'
[INFO] [1666147050.545963454] [minimal_publisher]: Publishing: 'Hello, world! 3'
...
```

In another terminal, run the dev-env container

```
ros-test/ros-compose/development$ docker compose run dev-env
```
and launch the listener
```
~/dev_ws# ./install/cpp_sub/lib/cpp_sub/listener 
[INFO] [1666147652.475020858] [minimal_subscriber]: I heard: 'Hello, world! 0'
[INFO] [1666147654.474300864] [minimal_subscriber]: I heard: 'Hello, world! 1'
[INFO] [1666147656.474448521] [minimal_subscriber]: I heard: 'Hello, world! 2'
[INFO] [1666147658.474358158] [minimal_subscriber]: I heard: 'Hello, world! 3'
...
```