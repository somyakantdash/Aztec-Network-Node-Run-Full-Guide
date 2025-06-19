# Aztec Network Sequencer Node Run Full Guide (PC and VPS)

### Offical Docs Guide - https://docs.aztec.network/next/the_aztec_network/guides/run_nodes/how_to_run_sequencer

----

## 🧰 Prerequisites
### Before getting started, make sure you have the following:
	
 * Create New Metamask Wallet
 * Claim Sepolia Eth Faucet in ur New Wallet Minimum 3 ETH [HERE](https://tinyurl.com/3srrcx95).

-------------
## Getting Sepolia ETH 
* Alchemy Faucet [HERE](https://www.alchemy.com/faucets/ethereum-sepolia)
* Pow Faucet -- [HERE](https://sepolia-faucet.pk910.de/)
* Google FAUCET -- [HERE](https://cloud.google.com/application/web3/faucet/ethereum/sepolia)
------------

---

1️⃣ Dependencies for WINDOWS & LINUX & VPS
```
sudo apt-get update && sudo apt-get upgrade -y
```
```
sudo apt install curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev  -y
```

2️⃣ Install Aztec Tools
```
bash -i <(curl -s https://install.aztec.network)
```
![440142117-610b5091-e8d5-45ac-9c9d-de26d080196e](https://github.com/user-attachments/assets/172299e5-9562-498e-a3af-420618cc6886)

3️⃣ Add Aztec to PATH
```
echo 'export PATH="$HOME/.aztec/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```
![440142705-be70b89b-e644-4d75-9087-1352cd544ad5](https://github.com/user-attachments/assets/fd5b6f95-e248-49cd-a188-0d573136e667)

Check version 
```
aztec
```

Update version 
```
aztec-up alpha-testnet
```

4️⃣ Obtain RPC URLs

### Sepolia RPC URL (I use Alchemy)

It's Free RPC (u get errors after some time)

### 🍀Alchemy: https://dashboard.alchemy.com/

👉Login/Sign Up

👉Click on `Create New app` > Give a name, Select Ethereum and `Create App` > Click on `Network` tab and select Sepolia > Copy the RPC, will be needed soon

![Screenshot 2025-05-07 112101](https://github.com/user-attachments/assets/985af9c3-35cb-4eb9-afba-b32f6b886315)
![image](https://github.com/user-attachments/assets/c2eee62c-ec39-450c-aed8-e2a2eb5deee0)


It's Paid RPC (rare chance u get any errors)

### 🍀NodeReal: https://nodereal.io/invite/ff92db1c-3f19-4df7-8c32-4d87a3030583

👉Create Account with Discord Or Github > Create New API Key > Click On That Key > Click Ethereum RPC Endpoint > Use Sepolia Https RPC Key

![Screenshot 2025-05-13 183626](https://github.com/user-attachments/assets/24e00e4e-5a9b-4cf4-ad53-b171916addfd)
![Screenshot 2025-05-13 183643](https://github.com/user-attachments/assets/8a43f82c-9b83-4e2e-b36f-4155e88a15b2)
![Screenshot 2025-05-13 183658](https://github.com/user-attachments/assets/aa78d4fe-f595-4483-80e2-3b097cfebd97)

-----
### Beacon RPC/L1 Consensus   

It's Free RPC (u get errors after some time)

* Use:   `https://rpc.drpc.org/eth/sepolia/beacon`
 OR
* Use:    `https://lodestar-sepolia.chainsafe.io`

It's Paid RPC (rare chance u get any errors)

### 🍀DRPC: https://drpc.org?ref=96acbf

👉Create new account by using Gmail > Click "Add Key" > Search Beacon & Copy ur ETH Sepolia Beacon RPC (It's Free)

👉U can Upgrage ur account by paying some $ to get more requests ($6 / ~1M requests)

![Screenshot 2025-05-11 144148](https://github.com/user-attachments/assets/8b72ed61-e786-4804-b827-716bec6d54e9)
![Screenshot 2025-05-11 144130](https://github.com/user-attachments/assets/176506c6-662c-40e3-9832-a275e98ad302)

### 🍀Ankr: https://www.ankr.com/rpc/?utm_referral=rTKuee6mUf

👉Create new account by using Gmail or Github > Click "API Credits" & Buy Some Credits (check below ss)

👉Click "Default Project" or Create New Project > Then Search ETH Testnet Sepolia Beacon RPC (It's Paid $10 / ~500k req)

![sdgsdg](https://github.com/user-attachments/assets/5cb99571-3ec5-4dc4-b599-45e3961699a4)
![dfgdg](https://github.com/user-attachments/assets/fe56d45e-f37e-4fd2-a6e5-0f5cea4a42d0)

![dgd](https://github.com/user-attachments/assets/f21791c8-a877-4b18-b363-e036d9cc2375)
![fghfg](https://github.com/user-attachments/assets/d8f3b8b8-bcd3-4fa1-9961-2c4cf7fcd86b)



5️⃣ Check IP (for Local PC)
```
curl ipinfo.io/ip
```
```
curl ifconfig.me
```
Copy the IP, will be needed soon

6️⃣ Enable Firewall & Open Ports
```
sudo ufw allow ssh
sudo ufw enable

sudo ufw allow 40400
sudo ufw allow 40500
sudo ufw allow 8080
```

For VPS Only
```
apt install screen -y
```
```
screen -S aztecSequencer
```
- PRESS CTRL+A+D (to run ur node continuously)
- To check ur Node Again
```
screen -r aztecSequencer
```

7️⃣ Start Node
```
aztec start --node --archiver --sequencer \
  --network alpha-testnet \
  --l1-rpc-urls RPC_URL  \
  --l1-consensus-host-urls BEACON_URL \
  --sequencer.validatorPrivateKey YourPrivateKey \
  --sequencer.coinbase YourevmAddress \
  --p2p.p2pIp IP
  --p2p.maxTxPoolSize 1000000000
```

Replace the following variables before you Run Node:
* `RPC_URL` & `BEACON_URL`: Step 4
* `YourPrivateKey`: Your EVM wallet private key (with 0x prefix)
* `YourAddress`: Your EVM wallet public address
* `IP`: Your server IP (Step 5)

After entering the command, your node starts running, It takes a few hours for your node to get sync to the tip of the block and mostly depend on how powerful your device is.

##  Getting Apprentice Role on Discord

Make sure the Node is Synced to the tip - [Confirm from here](https://aztecscan.xyz/)

![image](https://github.com/user-attachments/assets/cea509d2-d0fe-4345-a32b-a9d18da4a3cb)

and compare with the Node

![image](https://github.com/user-attachments/assets/19b73911-3855-4795-baa8-8a2bf643e463)


+ Open a new Ubuntu screen (Make sure the Node is already running).

*Step 1: Get the latest proven block number:*
```bash
curl -s -X POST -H 'Content-Type: application/json' \
-d '{"jsonrpc":"2.0","method":"node_getL2Tips","params":[],"id":67}' \
http://localhost:8080 | jq -r ".result.proven.number"
```
* Save this block number for the next steps
* Example output: 23546

**Step 2: Generate your sync proof**
```bash
curl -s -X POST -H 'Content-Type: application/json' \
-d '{"jsonrpc":"2.0","method":"node_getArchiveSiblingPath","params":["BLOCK_NUMBER","BLOCK_NUMBER"],"id":67}' \
http://localhost:8080 | jq -r ".result"
```
* Replace 2x `BLOCK_NUMBER` with your number, the output from step1 above

![440303878-b6479b17-b94f-4914-9320-66d6b0afd0e5](https://github.com/user-attachments/assets/0d4e2512-1557-42a6-8ec7-1423bb744c78)

**Step 3: Register with Discord**
* Type the following command in this Discord server: `/operator start`
* After typing the command, Discord will display option fields that look like this:
* `address`:            Your validator address (Ethereum Address)
* `block-number`:      Block number for verification (Block number from Step 1)
* `proof`:             Your sync proof (base64 string from Step 2)

* Once you paste the proof, ensure your cursor is out of the proof details before you click on send to avoid the send button adding a gap to the details which will invlidate your proof

* After submission, you'll get your `Apprentice` Role


https://github.com/user-attachments/assets/7359be63-62bb-4951-8624-7175bd2a2bf0

  * Visit the [Discord channel](https://discord.com/invite/aztec)
  * Follow the Video guide
  * Start the `Operator` with the `/operator start` then select follow the video guide

--------

## Register as Validator
```
aztec add-l1-validator \
  --l1-rpc-urls SEPOLIA-RPC-URL \
  --private-key YOUR-PRIVATE-KEY \
  --attester YOUR-VALIDATOR-ADDRESS \
  --proposer-eoa YOUR-VALIDATOR-ADDRESS \
  --staking-asset-handler 0xF739D03e98e23A7B65940848aBA8921fF3bAc4b2 \
  --l1-chain-id 11155111
```
Replace `SEPOLIA-RPC-URL` , `YOUR-PRIVATE-KEY` , `YOUR-VALIDATOR-ADDRESS` with actual value and then then proceed it

## 🔶For Next Day Run This Command (Windows)

#1 Open WSL and Put this Command 
```
aztec start --node --archiver --sequencer \
  --network alpha-testnet \
  --l1-rpc-urls RPC_URL  \
  --l1-consensus-host-urls BEACON_URL \
  --sequencer.validatorPrivateKey YourPrivateKey \
  --sequencer.coinbase YourevmAddress \
  --p2p.p2pIp IP
  --p2p.maxTxPoolSize 1000000000
```

Replace the following variables before you Run Node:
* `RPC_URL` & `BEACON_URL`: Step 4
* `YourPrivateKey`: Your EVM wallet private key (with 0x prefix)
* `YourAddress`: Your EVM wallet public address
* `IP`: Your server IP (Step 5)

## Delete Node File
```
rm -r /root/.aztec
```

## Need to Free Your 8080 Port

### Identify the Process Using Port 8080
```
sudo ss -tulpn | grep 8080
```

Example - ``` LISTEN  0  128  0.0.0.0:0380  0.0.0.0:*  users:(("nginx",pid=1234,fd=6)) ```

### Terminate the Process by PID
```
sudo kill -9 1234
```

### Kill All Processes Using Port 8080
```
sudo fuser -k 8080/tcp
```

Reference Video How to Free 8080 or any port - https://youtu.be/4iP4GvLfCrU?t=229


## If U Getting This Error

![6127552180060801396](https://github.com/user-attachments/assets/43c20d1f-197f-4000-9c8b-ec593ea59cb6)

Press CTRL + C to stop Node

Delete Database
```
rm -rf ~/.aztec/alpha-testnet/data/ 
```

Update NODE
```
aztec-up alpha-testnet
```

Restart Your Node (using beacon paid rpc only to solve this issue)
```
aztec start --node --archiver --sequencer \
  --network alpha-testnet \
  --l1-rpc-urls RPC_URL  \
  --l1-consensus-host-urls BEACON_URL \
  --sequencer.validatorPrivateKey YourPrivateKey \
  --sequencer.coinbase YourevmAddress \
  --p2p.p2pIp IP
  --p2p.maxTxPoolSize 1000000000
```

Replace the following variables before you Run Node:
* `RPC_URL` & `BEACON_URL`: Step 4
* `YourPrivateKey`: Your EVM wallet private key (with 0x prefix)
* `YourAddress`: Your EVM wallet public address
* `IP`: Your server IP (Step 5)

### You’re getting a TypeError: fetch failed → ConnectTimeoutError, which means the Aztec node can’t reach external resources (likely the L1 RPC or bootnode URLs).
![image](https://github.com/user-attachments/assets/0ae5dbdb-da0c-49fa-9299-d8cf0d964b55)


* Enable UFW

```
sudo ufw enable
```

* Allow Outbound connections

```
sudo ufw default allow outgoing
sudo ufw default allow incoming
```

* Readd and reload

```
sudo ufw allow 22/tcp      
sudo ufw allow 8080/tcp     
sudo ufw allow 40400/tcp   
sudo ufw allow 40400/udp
sudo ufw allow 40500/tcp 
```

```
sudo ufw reload
sudo ufw status verbose
```

### Now start Node again by Start Node Command


## Upgrade to v0.87.9 🧃

Move to Aztec Screen (If u Run Node in VPS

```
screen -r aztecSequencer
```

Stop your node if already running
```
ctrl+c
```

Upgrade Your Node
```
aztec-up latest
```

Start your node with `Start` command (using beacon paid rpc only to solve this issue)
```
aztec start --node --archiver --sequencer \
  --network alpha-testnet \
  --l1-rpc-urls RPC_URL  \
  --l1-consensus-host-urls BEACON_URL \
  --sequencer.validatorPrivateKey YourPrivateKey \
  --sequencer.coinbase YourevmAddress \
  --p2p.p2pIp IP
  --p2p.maxTxPoolSize 1000000000
```

Replace the following variables before you Run Node:
* `RPC_URL` & `BEACON_URL`: Step 4
* `YourPrivateKey`: Your EVM wallet private key (with 0x prefix)
* `YourAddress`: Your EVM wallet public address
* `IP`: Your server IP (Step 5)
