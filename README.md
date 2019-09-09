# Nexycoin
Example Cryptocurrency elaborating on my [general-purpose-blockchain](https://github.com/lukegniwecki/general-purpose-blockchain) repo.

The code includes the addition of *transactions* as well as a few new classess and functions (see below). 

This cryptocurrency uses the Proof of Work consensus mechanism. 

## Required
**Python 3.6**

**Flask:** install in terminal 
```pip install Flask==0.12.2```

Flask quickstart guide: ```https://flask.palletsprojects.com/en/1.0.x/quickstart/```

**Requests:** install in terminal
```pip install requests==2.18.4```

**Postman HTTP Client:**
```https://www.getpostman.com```

## Libraries 
Libraries imported into Python and used throughout the codebase:
- datetime - needed for time stamping blocks in Unix time timestamp
- hashlib - used to hash the blocks
- json - used to encode the blocks before they are hashed
- Flask - Flask class from the flask library used to create a web application 
- jsonify - used to return messages in postman when requesting the state of the blockchain or key info of the block that has been mined 
- requests (Flask) - added to flask libraries. This module is needed to use a GET json function to connect the nodes on decentralised network.
- requests (Python) - required to check that all nodes have the same chain which will be used to apply the consensus
- uuid4 (from uuid) -  equired to create an address for each node on the network
- urlparse (from urllib.parse) - needed to parse the URL of each of the nodes

## Converting a Blockchain into a Cryptocurrency 
**Adding Transactions**

`self.transactions = []` - list of transactions to be created in the *init* method and before the `self.create_block` function

`add_transaction(self, sender, receiver, amount)` - method for adding transactions

**Creating Consensus**

`self.nodes = set()` - node for the init method (must be an empty set)

`add_node(self, address)` - add node method for adding a new node to the network 

`replace_chain(self):` - required to apply the consensus and replace the chain with the longest one 

The above method contains *self* as the function is called in a specific node.

**Updating the Mining Function**

`blockchain.add_transaction(sender = node_address, receiver = 'Luke G.', amount = 10` - update to the `mine_block():` function. *Receiver* is the miner whereas *amount* is the mining reward. 

## Setting Up Nodes (Decentralising Nexycoin)

## Testing 

## Requests 
Postman requests used to query the blockchain, add transactions and apply the consensus once the application is running on Flask.

### GET

**Get Chain** 
- Queries the current state of blockchain: http://127.0.0.1:5000/get_chain

**Mine Block**
- Mines a new block: http://127.0.0.1:5000/mine_block

**Is Chain Valid** 
- Checks if Blockchain is valid i.e. if all previous hashes match with corresponding blocks: http://127.0.0.1:5000/is_chain_valid 

### POST  

