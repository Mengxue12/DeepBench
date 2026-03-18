

# install docker

```bash
# download 
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

# add current user to docker group
sudo usermod -aG docker $USER

# reboot or use the command:
newgrp docker
```

check version and validate

```bash
docker --version

# run a container
docker run hello-world
```

auto run setting 
```bash
sudo systemctl enable docker
sudo systemctl start docker
```


# build ComputeLibrary

```bash
scons arch=arm64-v8a build=native neon=1 Werror=0 -j4
```
(it takes a long time ~ 2 hours)

# build benchmarks binary

```bash
make xxx
```

# build docker image

```bash
docker build -t mengxue12/deepbench-arm:0.3 --push .
```
