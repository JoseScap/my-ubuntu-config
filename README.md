## Visual Studio Code

1. Download from [here](https://code.visualstudio.com/)
2. Install .deb file using dpkg

```bash
sudo dpkg -i <package path>
```

## Git

1. Run next command

```bash
sudo apt-get install git
```

## Azure CLI

1. Get packages needed for the installation process:

```bash
sudo apt-get update
sudo apt-get install ca-certificates curl apt-transport-https lsb-release gnupg
```

2. Download and install the Microsoft signing key:

```bash
sudo mkdir -p /etc/apt/keyrings
curl -sLS https://packages.microsoft.com/keys/microsoft.asc |
    gpg --dearmor |
    sudo tee /etc/apt/keyrings/microsoft.gpg > /dev/null
sudo chmod go+r /etc/apt/keyrings/microsoft.gpg
```

3. Add the Azure CLI software repository: 

```bash
AZ_DIST=$(lsb_release -cs)
echo "deb [arch=`dpkg --print-architecture` signed-by=/etc/apt/keyrings/microsoft.gpg] https://packages.microsoft.com/repos/azure-cli/ $AZ_DIST main" |
    sudo tee /etc/apt/sources.list.d/azure-cli.list
```

4. Update repository information and install the azure-cli package:

```bash
sudo apt-get update
sudo apt-get install azure-cli
```

## Docker Engine

1. Run the following command to uninstall all conflicting packages:

```bash
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```

2. Set up Docker's apt repository.

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

3. Install the Docker packages.

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

4. Verify that the Docker Engine installation is successful by running the hello-world image.

```bash
sudo docker run hello-world
```

5. Enter the command below to create the docker group on the system.

```bash
sudo groupadd -f docker
```

6. Type the following usermod command to add the active user to the docker group.

```bash
sudo usermod -aG docker $USER
```

7. Apply the group changes to the current terminal session by typing:

```bash
newgrp docker
```

8. Check if the docker group is in the list of user groups.

```bash
groups
```