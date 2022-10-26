# Docker Compose to Build Production Environment Containers

Build production containers, publish and subscribe. The `cpp_pub` and `cpp_sub` packages from the install folder are copied over from the `dev-env` container.
```
ros-test/ros-compose/production$ docker compose build
```

Run the publish and subscribe containers.
```
ros-test/ros-compose/production$ docker compose up
[+] Running 3/3
 ⠿ Network production_default           Created                                                                                                    0.0s
 ⠿ Container production-prod-env-sub-1  Created                                                                                                    0.1s
 ⠿ Container production-prod-env-pub-1  Created                                                                                                    0.1s
Attaching to production-prod-env-pub-1, production-prod-env-sub-1
production-prod-env-pub-1  | [INFO] [launch]: All log files can be found below /root/.ros/log/2022-10-26-04-03-14-530126-3a44ebd219ff-1
production-prod-env-pub-1  | [INFO] [launch]: Default logging verbosity is set to INFO
production-prod-env-sub-1  | [INFO] [launch]: All log files can be found below /root/.ros/log/2022-10-26-04-03-14-531691-6214ce4b77f0-1
production-prod-env-sub-1  | [INFO] [launch]: Default logging verbosity is set to INFO
production-prod-env-pub-1  | [INFO] [talker-1]: process started with pid [49]
production-prod-env-sub-1  | [INFO] [listener-1]: process started with pid [49]
production-prod-env-pub-1  | [talker-1] [INFO] [1666756996.680030798] [minimal_publisher]: Publishing: 'Hello, world! 0'
production-prod-env-sub-1  | [listener-1] [INFO] [1666756996.680901572] [minimal_subscriber]: I heard: 'Hello, world! 0'
production-prod-env-pub-1  | [talker-1] [INFO] [1666756998.679838803] [minimal_publisher]: Publishing: 'Hello, world! 1'
production-prod-env-sub-1  | [listener-1] [INFO] [1666756998.680299056] [minimal_subscriber]: I heard: 'Hello, world! 1'
production-prod-env-pub-1  | [talker-1] [INFO] [1666757000.680118978] [minimal_publisher]: Publishing: 'Hello, world! 2'
production-prod-env-sub-1  | [listener-1] [INFO] [1666757000.680684752] [minimal_subscriber]: I heard: 'Hello, world! 2'
...
```