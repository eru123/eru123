# Installing docker on Ubuntu 20.04

### Using snap

```bash
sudo snap install docker
```

### Using apt

```bash
sudo apt  install docker.io 
```

### Fixing docker permission
```bash
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
docker images
sudo reboot
```

### Loging in to Docker Hub
```bash
docker login
```
