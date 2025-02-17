# Dicoogle Devops 

Dicoogle DevOps provides a Docker-based environment to build and deploy Dicoogle along with its plugins. This repository contains all necessary Docker Compose configurations and scripts to streamline your development and deployment process.


## Build plugins

Before running Dicoogle, build the plugins container. This step compiles and prepares all necessary plugins:


```
docker compose build plugins-builder --no-cache --progress plain
docker compose up plugins-builder
```


## Run 

After successfully building the plugins, you can start the Dicoogle service in detached mode:


```
 docker compose up dicoogle -d
```


## Additional Commands

- **Stop Services:** To stop and remove all running containers:
  
```bash
  docker compose down
```

- **View Logs:** To view logs for a specific service (e.g., Dicoogle):
  
```bash
  docker compose logs dicoogle
```
