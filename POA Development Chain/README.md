# Proof of Authority Development Chain

## New job at ZBank
Our first project at the company is to set up a private testnet that our team of developers can use to explore potentials for blockchain at ZBank. We are setting up a testnet because:
- There is no real money involved, which will gives the developers the freedom to experiment.
- Testnets allows for offline development.

In order to set up a testnet, we will need to use the following skills/tools we learned in class:

- Puppeth, to generate your genesis block.
- Geth, a command-line tool, to create keys, initialize nodes, and connect the nodes together.
- The Clique Proof of Authority algorithm.

Please note, tokens inherently have no value here, so we will provide pre-configured accounts and nodes for easy setup.

## Environment setup requirements:

- MyCrypto Desktop App, available to download from [here](https://download.mycrypto.com/)
- Go Ethereum Tools, available to download from [here](https://geth.ethereum.org/downloads/)

Important Note: Windows users MUST use git-bash and not the default Windows command prompt when you are requested to open the terminal window to execute commands.

## Step 1: Create accounts for two nodes
We will try generate two new nodes with new account addresses that will serve as our pre-approved sealer addresses:

![Create Nodes](https://github.com/Sadiakbar/Blockchain-Homework/blob/main/POA%20Development%20Chain/Cryptozone/Screenshots/Create%20Nodes.jpg)

- Using git-bash we will navigate to the folder where we have saved the Go Ethereum Tools as 'Blockchain-Tools' and create accounts for two nodes for the network with a separate datadir for each using geth:
 - ./geth --datadir node1 account new
 - ./geth --datadir node2 account new
- Save the public address of each node and path of the secretkey file and the password used to unlock the secretkey file on a separate document.

## Step 2: Generate a new genesis block
We will use run Puppeth to generate a new genesis block, and the we will need the addresses we noted above:
- Using git-bash, in the same path where we created the node1 and node2, we typed "./puppeth" to run the puppeth configuration.
- Next, we chose'cryptozone' as our NETWORK NAME and selected the option to configure a new genesis block
- We ran the Clique (Proof of Authority) consensus algorithm.
- For our next command we input the account addresses from Step 1; to seal, and to pre-fund.
- We chose 'no' for pre-funding the pre-compiled accounts (0x1 .. 0xff) with wei to keep the genesis cleaner.
- When back at the main menu, we chose the "Manage existing genesis" option and exported genesis configurations. However, only 2 out of 4 files were created, but we only needed cryptozone.json for the steps to follow.

![Puppeth configuration 1](https://github.com/Sadiakbar/Blockchain-Homework/blob/main/POA%20Development%20Chain/Cryptozone/Screenshots/Puppeth%20configuration%201.jpg)


![Puppeth configuration 2](https://github.com/Sadiakbar/Blockchain-Homework/blob/main/POA%20Development%20Chain/Cryptozone/Screenshots/Puppeth%20configuration%202.jpg)


## Step 3: Initialize each node
After the genesis block was created, we worked on initiliazing each node using the following commands:
- ./geth init cryptozone/cryptozone.json --datadir node1
- ./geth init cryptozone/cryptozone.json --datadir node2

![Initialize nodes](https://github.com/Sadiakbar/Blockchain-Homework/blob/main/POA%20Development%20Chain/Cryptozone/Screenshots/Initialize%20Nodes.jpg)


## Step 4: Begin mining
After initializing we ran the following commands in separate terminals to begin mining:
For node 1, using just the address of node1:
- ./geth --datadir node1 --unlock "0xCCA63f2794e95d3Eb5b2c367b020A37c5E5Cd152" --mine --rpc --allow-insecure-unlock

![Run node1](https://github.com/Sadiakbar/Blockchain-Homework/blob/main/POA%20Development%20Chain/Cryptozone/Screenshots/Run%20node1.jpg)

For node 2, we will incorporate the enode address of node1
- ./geth --datadir node2 --unlock "0x09C701A4381c6947F666B11418400EaE5010Cc92" --mine --port 30304 –bootnodes "enode://08cd680e5b4a078bc2ad132dfed807078f4fc042c4d84c53f356eaf5e9e461b5af64c3dd0657c8d481874c3e8b6669325df6150f5da29477c15b0dc946e856ea@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock

![Run node2](https://github.com/Sadiakbar/Blockchain-Homework/blob/main/POA%20Development%20Chain/Cryptozone/Screenshots/Run%20node2.jpg)


![Custom Node](https://github.com/Sadiakbar/Blockchain-Homework/blob/main/POA%20Development%20Chain/Cryptozone/Screenshots/Custom%20Node.gif)
![My Wallet](https://github.com/Sadiakbar/Blockchain-Homework/blob/main/POA%20Development%20Chain/Cryptozone/Screenshots/My%20Wallet.gif)
![My Crypto Wallet](https://github.com/Sadiakbar/Blockchain-Homework/blob/main/POA%20Development%20Chain/Cryptozone/Screenshots/My%20Crypto%20Wallet.jpg)
![TX status](https://github.com/Sadiakbar/Blockchain-Homework/blob/main/POA%20Development%20Chain/Cryptozone/Screenshots/TX%20status.gif)


