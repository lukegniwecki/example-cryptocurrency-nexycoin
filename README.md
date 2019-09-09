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

## Converting Blockchain into Cryptocurrency 
**1. Adding Transactions**

`self.transactions = []` - list of transactions to be created in the *init* method and before the `self.create_block` function

`add_transaction(self, sender, receiver, amount)` - method for adding transactions

**2. Creating Consensus**

`self.nodes = set()` - node for the init method (must be an empty set)

`add_node(self, address)` - add node method for adding a new node to the network 

`replace_chain(self):` - required to apply the consensus and replace the chain with the longest one 

The above method contains *self* as the function is called in a specific node.

**3. Specifying Mining Reward**

`blockchain.add_transaction(sender = node_address, receiver = 'Luke G.', amount = 10` - update to the `mine_block():` function 

*receiver* = miner 

*amount* = mining reward

**4. Creating Uinque Node Address**

`node_address = str(uuid4()).replace('-', '')` - creates a unique node address using the *uuid* library

## Running the Blockchain and Creating Transactions
The included *.json* files contain (1) example node addresses (*[nodes.json](https://github.com/lukegniwecki/example-cryptocurrency-nexycoin/blob/master/nodes.json)*) and the format of the transaction (*[transaction.json](https://github.com/lukegniwecki/example-cryptocurrency-nexycoin/blob/master/transaction.json)*). 

There are three nodes in this example cryptocurrency. The use the following Flask addresses and ports: 

- **Node 1:** http://127.0.0.1:5001/ 

- **Node 2:** http://127.0.0.1:5002/ 

- **Node 3:** http://127.0.0.1:5003/  

Copies of the source (*[nexycoin_core.py](https://github.com/lukegniwecki/example-cryptocurrency-nexycoin/blob/master/nexycoin_core.py)*) have been created so we can decentralise the Nexycoin, mine blocks, send transactions and apply the consennsus: 

- **Node 1:** *[nexycoin_node_1_5001.py](https://github.com/lukegniwecki/example-cryptocurrency-nexycoin/blob/master/nexycoin_node_1_5001.py)*

- **Node 2:** *[nexycoin_node_2_5002.py](https://github.com/lukegniwecki/example-cryptocurrency-nexycoin/blob/master/nexycoin_node_2_5002.py)*

- **Node 3:** *[nexycoin_node_1_5003.py](https://github.com/lukegniwecki/example-cryptocurrency-nexycoin/blob/master/nexycoin_node_3_5003.py)*

## Requests 
Postman requests used to query the blockchain, add transactions and apply the consensus once the application is running on Flask. Port `5001`has been used in this example (*Node 1*). 

### GET

**Get Chain:** http://127.0.0.1:5001/get_chain 
- Queries the current state of blockchain

**Mine Block:** http://127.0.0.1:5001/mine_block
- Mines a new block

**Is Chain Valid:** http://127.0.0.1:5001/is_chain_valid 
- Checks if Blockchain is valid i.e. if all previous hashes match with corresponding blocks

**Replace Chain:** http://127.0.0.1:5001/replace_chain 
- Replaces the chain with the longest chain if the chain on the noode in question isn't up to date

### POST  

**Add Transaction:** http://127.0.0.1:5001/add_transaction 
- Announces the transaction onto the blockchain

**Connect Node:** http://127.0.0.1:5001/connect_node 
- Decentralises the network by connnecting nodes with each other
