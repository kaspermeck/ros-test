# Docker Compose to Build Production Environment Containers

Build production containers, publish and subscribe. The `talker` and `listener` binaries are copied over from the `dev-env` container.
```
ros-test/ros-compose/production$ docker compose build
```

Run the publish and subscribe containers.
```
ros-test/ros-compose/development$ docker compose up
[+] Running 2/0
 ⠿ Container production-prod-env-pub-1  Created                                                                                                    0.0s
 ⠿ Container production-prod-env-sub-1  Created                                                                                                    0.0s
Attaching to production-prod-env-pub-1, production-prod-env-sub-1
production-prod-env-pub-1  | [INFO] [1666149515.569333040] [minimal_publisher]: Publishing: 'Hello, world! 0'
production-prod-env-sub-1  | [INFO] [1666149515.570241272] [minimal_subscriber]: I heard: 'Hello, world! 0'
production-prod-env-pub-1  | [INFO] [1666149517.569571112] [minimal_publisher]: Publishing: 'Hello, world! 1'
production-prod-env-sub-1  | [INFO] [1666149517.570271054] [minimal_subscriber]: I heard: 'Hello, world! 1'
production-prod-env-pub-1  | [INFO] [1666149519.569717839] [minimal_publisher]: Publishing: 'Hello, world! 2'
production-prod-env-sub-1  | [INFO] [1666149519.570380408] [minimal_subscriber]: I heard: 'Hello, world! 2'
...
```