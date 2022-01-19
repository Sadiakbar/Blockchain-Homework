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
- Using git-bash we will navaigate to the folder where we have saved the Go Ethereum Tools as 'Blockchain-Tools' and create accounts for two nodes for the network with a separate datadir for each using geth:
 - ./geth --datadir node1 account new
 - ./geth --datadir node2 account new

![Create Nodes](https://github.com/Sadiakbar/Blockchain-Homework/blob/main/POA%20Development%20Chain/Cryptozone/Screenshots/Create%20Nodes.jpg)




Be sure to include all of the geth flags required to get both nodes to mine and explain what they mean.
Explain the configuration of the network, such as it's blocktime, chain ID, account passwords, ports, etc.
Explain how to connect MyCrypto to your network and demonstrate (via screenshots and steps) and send a transaction.
Upload the code, including the networkname.json and node folders.
