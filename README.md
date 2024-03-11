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