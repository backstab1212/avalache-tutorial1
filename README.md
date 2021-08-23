# How to mint your own ERC20 on Avalanche using Open Zeppelin
- [How to mint your own ERC20 on Avalanche using Open Zeppelin](#how-to-mint-your-own-erc20-on-avalanche-using-open-zeppelin)
	- [Introduction](#introduction)
	- [Requirement](#requirement)
	- [Setup Metamask](#setup-metamask)
				- [Adding Avalache Fuji Testnet network](#1-adding-avalache-fuji-testnet-network)
				- [Funding Avalanche wallet address](#2-funding-avalanche-wallet-address)
	- [Create Mintable Token](#create-mintable-token)
		- [Remix](#remix)
		- [1.Setting up new projects](#1setting-up-new-projects)
		- [2. Preset ERC20 Contract](#2-preset-erc20-contract)
		- [3. Deploy The Contract](#3-deploy-the-contract)
## Introduction
in this tutorial we will create erc20 with open zepplein framework thats run on Avalanche testnet network, we can interact with the token with call burn and sent to other address


## Requirement 
- [Metamask](https://metamask.io/download.html) 
- [Remix IDE (optionial)](https://remix.ethereum.org)
- [Open Zeppline](https://openzeppelin.com)


## Setup Metamask

 ### 1. **Adding Avalache Fuji Testnet network**
   if it's the first time for you using metamask, by default metamask runs on Etherium Mainnet so we need to change the network to Avalache Fuji Testnet network.

  ![Alt Text](https://raw.githubusercontent.com/backstab1212/avalache-tutorial1/main/src/gif/adding%20Avalache%20testnet%20Network.gif)
  + Network Name: Avalanche C-Chain
  + New RPC URL:
	+ Fuji Testnet: https://api.avax-test.network/ext/bc/C/rpc
	+ Local Testnet: http://localhost:9650/ext/bc/C/rpc 
  + ChainID:
	+ Fuji Testnet: 43113 
	+ Local Testnet: 43112 
  + Symbol: AVAX
  + Explorer:
	+ Fuji Testnet: https://cchain.explorer.avax-test.network
	+ Localnet: n/a 

 ### 2. **Funding Avalanche wallet address**
   creating  mintable token required some avax for handling transaction, we can easily get avax token by claiming on this [faucet](https://faucet.avax-test.network/)
   - make sure you are on avalanche C-chain Network
   - click on metamask under your wallet name in order to copy your wallet address
   - paste your wallet address on the box of field
   ![Alt Text](https://raw.githubusercontent.com/backstab1212/avalache-tutorial1/main/src/gif/Funding%20token.gif)
## Create Mintable Token
### Remix
Remix IDE is an open source web and desktop application. It fosters a fast development cycle and has a rich set of plugins with intuitive GUIs. Remix is used for the entire journey of contract development as well as being a playground for learning and teaching Ethereum.
further information please read this [Documentation](https://remix-ide.readthedocs.io/en/latest/#)

 ### 1.Setting up new projects
   it's time to create our smart contract, we can develop our smart contract thorugh web browser or Desktop Application 
   - [Remix web browser](https://remix.ethereum.org/)  
   - [Remix desktop application](https://github.com/ethereum/remix-desktop/releases)


when opened remix by default it's has bunch of file you can delete it and create a new workspace and create your own name of solidty file for importing [Preset ERC20 Contract](https://raw.githubusercontent.com/OpenZeppelin/openzeppelin-contracts/master/contracts/token/ERC20/presets/ERC20PresetMinterPauser.sol) from openzeppline

![Alt Text](https://raw.githubusercontent.com/backstab1212/avalache-tutorial1/main/src/gif/Solidity.gif)

### 2. Preset ERC20 Contract
It is preset to allow for token minting (create), stop all token transfers (pause) and allow holders to burn (destroy) their tokens. The contract uses [Access Control](https://docs.openzeppelin.com/contracts/4.x/access-control) to control access to the minting and pausing functionality. The account that deploys the contract will be granted the minter and pauser roles, as well as the default admin role.
This contract is ready to deploy without having to write any Solidity code. It can be used as-is for quick prototyping and testing, but is also suitable for production environments.
	for further information you can visit this [documentation](https://docs.openzeppelin.com/contracts/4.x/erc20)


  - copy and paste this code to the new solidity file that we create before
``` solidity
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/presets/ERC20PresetMinterPauser.sol"
```
  - press Ctrl+S to save and it will automaticly importing the preset 
  - click on the preset erc20 contract
  	![alt text](https://raw.githubusercontent.com/backstab1212/avalache-tutorial1/main/src/gif/Preset%20ERC20%20Contract.gif)


### 3. Deploy The Contract
1.  first we need to check the version of solidity compiler make sure the version it's above the required version of the preset Erc20 contract 

	![alt text](https://raw.githubusercontent.com/backstab1212/avalache-tutorial1/main/src/gif/SolidityCompiler.gif)

+ connect remix to metamask, we need to change the enviroment to injected web 3, confirm it, and we will see our wallet address on the account section
  ![alt text](https://raw.githubusercontent.com/backstab1212/avalache-tutorial1/main/src/gif/Connect%20to%20metamask.gif)
+ select erc20 preset minter from dropdown contract
+ name your token and symbol in my case i use "AVAXTESTING""AT"
+ transact/deploy and a pop out will come out just confirm it 
+ confirm on metamask
+ copy the transaction hash from remix console 
  ![alt text](https://raw.githubusercontent.com/backstab1212/avalache-tutorial1/main/src/gif/Name%20and%20symbol.gif)

lets check our transaction hash on [testnet explorer](https://cchain.explorer.avax-test.network/) and add the token to our wallet address
![alt text](https://raw.githubusercontent.com/backstab1212/avalache-tutorial1/main/src/gif/Adding%20token%20on%20Metamask.gif)

we already add the token contracts but it has 0 balance so let mint some token to our wallet make sure you are entered the amount in wei 1000000000000000000000=1000 token

![alt text](https://raw.githubusercontent.com/backstab1212/avalache-tutorial1/main/src/gif/Mint%20the%20token.gif)
