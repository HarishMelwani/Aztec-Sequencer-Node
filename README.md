<div align="left">

# 👨🏻‍💻 **Aztec Sequencer Guide** 👨🏻‍💻

</div>

# 🖥️ Device/System Requirements 

![image](https://github.com/user-attachments/assets/9e7e78a8-ddeb-4e0b-90a8-46f2ab5886b3)



# Pre-Requirements 🛠

- Docker & Docker Compose

   🔺(Let run your docker in background if u are using local Device)

- Aztec Tool

- Sepolia RPC URL

- Beacon RPC 



# Install Required Dependecies

```
sudo apt-get update && sudo apt-get upgrade -y
```

* Install Node.js 

```
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - && sudo apt update && sudo apt install -y nodejs
```

* Other Packages

```
sudo apt install curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev screen ufw -y
```


# Install Docker & Docker Compose


```
sudo apt update && sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

```
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```
sudo apt update && sudo apt install -y docker-ce && sudo systemctl enable --now docker
```

```
sudo usermod -aG docker $USER && newgrp docker
```


```
sudo curl -L "https://github.com/docker/compose/releases/download/$(curl -s https://api.github.com/repos/docker/compose/releases/latest | jq -r .tag_name)/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && sudo chmod +x /usr/local/bin/docker-compose
```


*  Verify installation

```
docker --version && docker-compose --version
```



# Install the Aztec CLI

```
bash -i <(curl -s https://install.aztec.network)
```


* Lets Config it to your corrent Shell/Path

```
echo 'export PATH="$HOME/.aztec/bin:$PATH"' >> ~/.bashrc
```

```
source ~/.bashrc
```

* Verify the Installation with-

```
aztec -h
```


* Set the correct version for the testnet

```
aztec-up latest
```


# Load your wallet with Sepolia Faucet 

https://sepolia-faucet.pk910.de/

https://www.alchemy.com/faucets/ethereum-sepolia



# Allow Incoming connections on Ports 

```
sudo ufw allow 22
sudo ufw allow ssh
sudo ufw enable
```

```
sudo ufw allow 40400
sudo ufw allow 8080
```


* Sites To Get Sepolia & Beacon RPC for free ( Rate Limit ) !

https://drpc.org/dashboard

https://developer.metamask.io/key/active-endpoints

https://www.alchemy.com


<div  align="center">
   
#  Start Your Sequencer 🍥

</div>

* Create a Screen Session

```
screen -S aztec
```

  🔺🔺--- Execute below given command to Start Your node & Dont forget to make changes in it-

```
aztec start --node --archiver --sequencer \
  --network alpha-testnet \
  --l1-rpc-urls Eth_Sepolia_RPC \
  --l1-consensus-host-urls Eth-beacon_sepolia_RPC \
  --sequencer.validatorPrivateKey 0xYourPrivateKey \
  --sequencer.coinbase YourAddress \
  --p2p.p2pIp Your_ip
```


* Replace `Eth_Sepolia_RPC` with your actual one!         -follow above steps

* Replace `Eth-beacon_sepolia_RPC` with your actual one            -follow above steps


* Replace `0xYourPrivateKey` with your actual EVM wallet pvt key    🔺 (dont forget to add 0x at starting)

* Replace `YourAddress` with your actual evm wallet address

* Replace `Your_ip` with your `External IP`  ... 

     -U can get External IP by running  `curl ifconfig.me`


* It will take time to Sync! 🥶

* The Successfull Running Should Look like this 👇


![Screenshot 2025-05-02 172143](https://github.com/user-attachments/assets/37ae2455-8b98-4642-bf14-0f5e1ed90cf2)


# Detached and Attached From the Screen

* For detached from screen session - `ctrl` , `a` + `d`

* For Attach - 

```
screen -r aztec
```

<div  align="left">
   
# Get Apprentice Role In Aztec dc- 😙

* join dc- https://discord.gg/aztec 

* Go to `#operators│start-here` Channel & react to the message to get your Apprentice Role.

   
# Register as a Validator 🔗⛓️

</div>

* Replace `Eth_Sepolia_Rpc` with your actual sepolia rpc url from Metamask developer.

* Replace `your-private-key` with your evm wallet pvt key! Dont forget  to add `0x` at starting

* Replace `your-validator-address` with your evm wallet address 

* Replace `your-validator-address` with your evm wallet address


```
aztec add-l1-validator \
  --l1-rpc-urls Eth_Sepolia_Rpc \
  --private-key your-private-key \
  --attester your-validator-address \
  --proposer-eoa your-validator-address \
  --staking-asset-handler 0xF739D03e98e23A7B65940848aBA8921fF3bAc4b2 \
  --l1-chain-id 11155111
```



* Note- ![image](https://github.com/user-attachments/assets/50e7e432-c2a1-4356-afe8-9d47a48f8e68)




👉 Follow me on X ( Twitter ) - https://x.com/harishmelwanii

If U have any issue please Dm me on X ~

Thank U! 👨🏻‍💻

Happy Coding💗
