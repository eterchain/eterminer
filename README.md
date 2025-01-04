# Eterchain Miner Binary Setup
* Official Guide : https://docs.eterchain.io
* This guide is for Linux AMD

## 1. Install Dependecies
```console
# Docker
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo chmod +x /usr/local/bin/docker-compose

# Docker version check
docker --version
```


## 2. Install Eterchain Miner
```console
cd ~
curl -L -O https://github.com/eterchain/eterminer/releases/download/v1.0.1/eterchainV1.0.0.tar.gz
```
```console
tar -xvzf eterchainV1.0.0.tar.gz
```
```console
cd eterminer
```

## 3. Run Eterchain Miner
```
./eterminer
```

## 4. Last Setup
**1. Enter your EVM wallet address**

**2. Pick a Pool from List**

## Optional: 
### Update Node
#### 1- Delete Old files
```
cd ~
rm -rf eterchainV1.0.0.tar.gz
rm -rf eterminer
```

#### 2- Stop Miner
**Stop Miner by ID**
```console
pgrep eterminer
# Example: if 575758, then use:
kill 575758
```

**Stop Miner by tmux session**
```console
tmux kill-session eterminer
```

### 3- Update and Rerun miner
Start from Step [Install Miner](https://github.com/eterchain/eterminer/edit/main/README.md#install-eterchain-miner)
