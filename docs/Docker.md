
## Docker

### Installing Docker

#### Desktop for windows

[Install Docker Desktop for Windows](https://docs.docker.com/docker-for-windows/install/)

#### Visual studio extension

[VS Market place](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)

[VS code extension](https://code.visualstudio.com/docs/containers/overview)

### Check status/info of docker

```sh
docker version
docker info
docker --help
```

### Download docker image using docker cli

[For microsoft sdk](https://hub.docker.com/_/microsoft-dotnet-sdk/)

```sh
docker pull mcr.microsoft.com/dotnet/sdk:5.0
```

### Docker running image in container

List images 

```sh
docker images
```

List containers

```sh
docker ps
```

-a includes even it is not active
```sh
docker ps -a
```

Creating container and running it

```sh
docker run -it --name MyFirstContainer <image-id-first3digit>
dotnet
dotnet --info
```

### Reference

[docker cli docs](https://docs.docker.com/engine/reference/commandline/images/)