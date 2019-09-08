# Nexycoin
Example Cryptocurrency elaborating on my [general-purpose-blockchain](https://github.com/lukegniwecki/general-purpose-blockchain) repo.

The code includes addition of `transactions` as well as a few new classess and functions (see below). 

## Required
Python 3.6

Flask: install in terminal 
```pip install Flask==0.12.2```

Flask quickstart guide: ```https://flask.palletsprojects.com/en/1.0.x/quickstart/```

Requests: install in terminal
```pip install requests==2.18.4```

Postman HTTP Client
```https://www.getpostman.com```

## Libraries
- datetime - needed for time stamping blocks in Unix time timestamp
- hashlib - used to hash the blocks
- json - used to encode the blocks before they are hashed
- Flask - Flask class from the flask library used to create a web application 
- jsonify - used to return messages in postman when requesting the state of the blockchain or key info of the block that has been mined 
- requests (Flask) - added to flask libraries. This module is needed to use its GET json function to connect the nodes on decentralised network.
- requests (Python) - required to check that all nodes have the same chain which will be used to apply the consensus
- uuid4 (from uuid) -  equired to create an address for each node on the network
- urlparse (from urllib.parse) - needed to parse the URL of each of the nodes

## Requests 
Requests used to query the blockchain in Postman once the application is running on Flask:

**Get Chain** 
- Queries the current state of blockchain: http://127.0.0.1:5000/get_chain

**Mine Block**
- Mines a new block: http://127.0.0.1:5000/mine_block

**Is Chain Valid** 
- Checks if Blockchain is valid i.e. if all previous hashes match with corresponding blocks: http://127.0.0.1:5000/is_chain_valid 

