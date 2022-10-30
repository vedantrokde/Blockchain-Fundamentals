# Blockchain-Fundamentals

## What is Blockchain and its working?
Need for Distributed Databases with Security and Trust as it eliminates need of middle service providers like banks in case of financial instruments and cryptocurrency came into existence.

Asymmetric Cryptography ensures security but lacks trust.
Ledger can ensure that data is properly mentored but this makes the database centralised but not distributed.
To overcome this ledger can be made available on each node.
But with readily avalability of ledger it becomes prone to being tampered.
Thus ultimatly we need a cyptographic security algorithm with ledger at every node with no tampering permissible and here come Blockchain in picture.

In blockchain we have long chain of blocks. A block contains some data that one stored can't be modified.
Hashing is cyptography algorithm. Different examples of hashing algorithm are MD5, SHA-256, SHA-512 etc.
Using hashing algorithm on a data generates a different key of same length most of the time. Some time generation of same hashing key leads to hash collision but it is a rare case. Thus every data has different hash and tampering with data will lead to change in hash value.

Lets say we have a block B1 of data D1 which has a hash key K1. Now when another block B2 of data D2+K1 has a hash K2. Later another block B3 of data D3+K2 has a hash K3 and so on. If somehow someone is able to tamper with data thus leading to changing even one single bit in any block from B1, B2, B3 is tampered this will lead to change in hash and can be easily verified with key present in succeding block. This makes blockchain an effective way of having distributed data with security and trust.

## Why Blockchain?
Taking an example of financial system in market today. If we are to send someone our money we tend to use services provided by banks. Wherein we keep our money with them and we are only charged for every transaction that we make. Thus to remove these middlemen services from the equation and have full control of over data we need a decentralised system. Thats why we tend to use blockchain.

## WEB3.0
Web on Decentralised (P2P) Network rather than using Client-Server network.

## CRYPTOGRAPHY
Blockchain works on peer-2-peer network (P2P). Unlike some of the major tech nowadays like facebook, banks etc these work on Client-Server network i.e., there is a centralised server or entity that keeps track of the transaction.

Some of the P2P network are Napster, Torrent etc. where we have peers and seeders who keep uploading and downloading the data file for proper transmission.

### Concerns with networking:
1. Confidentiality: In P2P, when a data is to be sent from A to B can alos be read by C.
2. Integrity: As C can read the original message transmitted from A, can also modify the data thus B receives modified version of data.
3. Non-repudiation: When in A-B data transmission, after B receives the data A declines being the sender.
4. Authentication: Data received by B is actually not sent by A but data has sender's address as A.

To solve these four issue we have Cryptography. Where in the concept of encryption and decryption is used. From the sender the data to be sent is first encrypted to get cipher text and later transmitted. Then this cipher text is received by the receiver which is now decrypted to get the original data. This encryption and decryption is done using key which can be a symmetric key cryptography or asymmetric key cryptography.

## Types of Cryptography
1. Symmetric Key Cryptography: Message sent by A is encrypted using key K1 and the message received by B is decrypted using key K1 only. This K1 key has to shared by some secured medium. For this cryptography we need one key for each of the node/user thus there will be n-number of keys and there management would be difficult.

2. Asymmetric/Public Key Cryptography: Here each user has a two keys i.e, public and private. For encryption public key is used and for decryption a private key is used. To send an encrypted message as public key is visible to everyone, sender encrypts using receiver's public key and then transmits the message on P2P network which when received at receiver's end only with his private key message can be decrypted whereas others receiving the data won't be able to decrypt the message.

> now to solve the issue of authentication we have digital signature

## DIGITAL SIGNATURE
Here in sender encrypts data with it's private key and receiver decrypts received cipher using sender's public key and thus validates the authentication of data. But in this process of single encrpytion the received data loses its confidentaility therefore double encryption process is used. Sender encrpyts data with it's private key first and then encrpyts again with receiver's public key. Now this double encrpyted data is sent over to receiver's end where receiver decrypts first with it's private key this ensures confidentiality and then decrypts using sender's public key thus ensuring authenticity of the data.

> Node: devices connected on the network are nodes.

### Two types of nodes:
1. Full Node: 
- A computer that contains entire blockchain(188GB as on 28/10/18) thus huge storage amount is required.
- Verifies each block before adding to blockchain.
- A full node can also be a miners (that runs mining software) then huge computing power is also needed.
- Miners are rewarded with transaction fee, i.e., insentives + bitcoins for every mined block(specific to bitcoin)
2. Partial/Light Node:
- Can be used for wallet purpose only, i.e., making transactions.

## HASHING
Hash Function: A mathematical function that converts arbiturary input string to fixed length unique output value. eg. MD6(message digest), SHA2-256(secure hashing algorithm), SHA3 etc. Even change in 1bit of input results in different hash value. Original input can't be deduced from hash value. Even though same hash values are merely impossible to obtain from two different input strings this case is termed as Hash Collision.

## MERKLE TREE
In a blockchain, all blocks are connected via hash values. One block contains transactions(one or many). For case of having many transaction data stored in a block hash of that block can be converted with combining all transaction data as one and then creating a unified hash value. Or hash for each of the transaction can be created and then these hashes can be combined to form hash value of block. To stores these all hash values we use Merkle Tree.
As per tree nomecleature we have root, leaf and parent/branch nodes. For each transactions, we place them at leaf and then take hash of subsequent pair combination of child nodes. In case of having no pair, single node is taken repeatedly. When keep on taking hashes of pair of child node, ultimately we reach to root of the tree. And now this root of merkle tree is hash value of whole block.

## BLOCKCHAIN ARCHITECTURE
Blockchain is basically a decentralised database. eg first public blockchain Bitcoin Blockchain. 

Block Data in this case will have transaction details like, To, From, Amount etc. 
Block Header is identification of a block that has timestamp, version, merkle root, difficulty traget, nonce, previous hash.

* Modification of a block will result to change in hash. This will create a problem and thus to make blockchain work we need to update hash in all the succeding block which requires lots of computing power(super computer is needed). This will lead to lack of security, which can be dealt with POW validation.
Thus to add a block we need validation which has a concept of POW(Proof Of Work) which deams to take atleast 10 mins to add a block in a blockchain. As blockchain will be stored on multiple machines each machine will have a copy of blockchain thus to make a modification it had to be verified by everyone, everyone should come in consensus to add a block. Here comes consensus algorithm to provide security. Hence with a super computer one will also need 50% majority of the blockchain network to alter any block. This makes blockchain secure.

* First block in a blockchain is called Genesis block that has previous block as 0.

## Types of Blockchain:
1. Public Blockchain: open and anyone can join blockchain
2. Private Blockchain: closed and company specific
3. Federated Blockchain: group of people/companies.

As for security reasons in a Public Blockchain POW is used that has 10min latency makes is slow. Whereas private blockchain provides access to restricted and authenticated users thus POW is not needed.

## CONSENSUS Algorithm
Blockchain being a distributed ledger thus in a network of mining nodes with all having copy of blockchain with exact same state. When a new block is to be added in the blockchain any node could do it and then the blockchain has to be copied to all other nodes but here there's problem of having malicious node. Thus a consensus vote is needed so that majority of nodes in network agree to adding the node. There are different consensus algorithm in play that differentiates block chain as Permissioned or Permissionless Blockchain.
In bitcoin the consensus algorithm is Proof of Work (PoW), in this all nodes spend some computation power doing some calculation and the node winning this can add the block and would receive bitcoin reward. Thus this job of doing compution lead to gaining trust of adding new block. But being in real world with lack so high computation power this process is expensive.
In ethereum the consensus algorithm is Proof of Stake(PoS), in which a node with higher stakes invested in the blockchain can add the block. As user with stakes invested won't risk losing than gaining.
Proof of Elapsed Time (PoET) by Intel or Proof of Deposit (PoD) or Proof of Capacity (PoC) are few more Consensus Algorithm.

## Proof of Work(PoW): 
Every competing node has to invest some computing power to win the chance of adding block to blockchain. This competition can be about doing some mathematical computation which shows that winner is not malicious. After winning the node gets bitcoin reward and thus be able to add block to blockchain. The mathematical calculation given has a complexity depending upon network size, active users and blockchain size. Thus PoW leads to computation exhaustion which is bad and also 51% attack by malicious nodes will lead to consensus thus blockchain can be hacked.

## ETHEREUM:
Bitcoin is the P2P electronic cash system(cryptocurrency). Whereas Ehtereum Blockchain has EVM(Ethereum Virtual Machine) which gives accessibilty for decentralised applications, i.e., dApps. Hence ethereum is the platform to run dApps which can be bought using Ether(cryptocurrency). An open platform to build software on using Solidity Programming Language. 

## Smart Contract:
A programming code written in ethereum that represents any type of contract is called Smart Contract. Many of the e-commerce website exists where we don't have basic trust. Thus using a smart contract, i.e., a prepaid order to an e-commerce company where I have paid the amount to contract but company hasn't received it. After the product is delivered and acknowledgement is received from my side amount will be paid to to company if not then i would receive my amount back. This smart contracts can be used in all markets saying automobile or insurance purchases through any middle man.

## NFT - Non-Fungible Token
Irreplacable Item. Having some sentimental or emotional value that can't be liquidated. NFTs are stored on blockchain and this can later be sold on my pricing to other buyer. Ethereum provides the platform service for this to prove validation of your ownership to that NFTs.

## Drawblocks of Blockchain:
1. Complex terminalogy and technology
2. Bitcoin or Ethereum carry out 7-10transactions/sec compared to VISA handling 1000s transactions/sec. Slow speed in public blockchain because of consensus algorithms eg 10mins in PoW.
3. PoW uses high computation, thus wastage of resources.
4. Security/Privacy: As data is publically available even though it is anonimously named everyone can see it.
5. 51% attack, more than half nodes in network are malicious will lead to blockchain being hacked.

## HYPERLEDGER
An open source collaborative effort created to advance cross-industry blockchain technology. It's a collaboration hosted by The Linux Foundation, including leaders in finance, banking, IoT, supply chains, manufacturing and technology. 
It is not a blockchain nor a company nor a cryptocurrency. It is a project. Public Blockchain like Bitcoin and Ethereum are B2C(Buisness to Consumer) model and are slow but blockchain technology can be used in B2B(Buisness to Buisness) model as well, i.e., enterprise market.
Hyperledger in these years of foundation has covered lots of ground and area of development. Sawtooth by Intel and Fabric are two popular open source framework along with some more like Iroha, Indy and Burrow. Few tools that can be used to create a Permissioned/Private Blockchain are Hyperledger Composer, Hyperledger Cello, Hyperledger Quilt, and Hyperledger Explorer.

## Smart Contract Code
To make transaction on a public blockchain we need to pay GAS fee/ transaction fee which will be rewarded to miners for the work they do. And on etherereum we need to buy ether that have gone costly nowadays thus for learning purpose test env of blockchain can be used. Using test network makes it free of cost.

1. Ethereum plugin - Metamask to use browser for blockchain
2. Install plugin and create or import A/C
3. Change env to test network and follow some process to add Ether to your account.
4. Visit remix.ethereum.org to write solidity code in .sol file
5. Write the code below and the compile and run in JS VM env. Hit deploy.
6. Under deployed play with graphical interface to deposit withdraw and getBalance functions.
7. To deploy on test network change JS VM env to Injection Web3 and deploy. Confirm ether payment popup.

> browser/bank.sol

```
pragma solidity 0.4.25

contract bank{
int bal;

constructor() public {
bal = 1; 
}

function getBalance() view public returns(int) {
return bal;
}

function withdraw(int amt) public {
bal = bal - amt;
}

function deposit(int amt) public {
bal = bal + amt;
}
}
```

> app/index.html - for frontend copy ABI from compiler page and address from Deployed Contract code

```
<!DOCTYPE html>
<html>
<head>
<script src="https://code.jquery.com/jquery-3.6.0.min.js" integrity="sha256-/xUj+3OJU5yExlq6GSYGSHk7tPXikynS7ogEvDej/m4=" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/gh/ethereum/web3.js@1.0.0-beta.34/dist/web3.min.js" crossorigin="anonymous"></script>
</head>
<body>
<div>
<input type="text" id="amount">
<p id="balance"></p>
<button id="deposit">Deposit</button>
<button id="withdraw">Withdraw</button>
</div>

<script>
var contract;
$(document).ready(function(){
web3 = new Web3(web3.currentProvider);
var address = "copy from deployed contract";
var abi = "abi from compiler page";
contract = new web3.eth.Contract(abi, address);

contract.methods.getBalance().call().then(function(bal){
$('#balance').html(bal);
})
})

$('#deposit').click(function(){
var amt=0;
amt = parseInt($('#amount').val());
web3.eth.getAccounts().then(function(accounts){
var acc = accounts[0];
return contract.methods.deposit(amt).send({from: acc});
}).then(function(res){ console.log(res); 
}).catch(function(err){ console.log(err); })
})

$('#withdraw').click(function(){
var amt=0;
amt = parseInt($('#amount').val());
web3.eth.getAccounts().then(function(accounts){
var acc = accounts[0];
return contract.methods.deposit(amt).send({from: acc});
}).then(function(res){ console.log(res); 
}).catch(function(err){ console.log(err); })
})

</script>
</body>
</html>
```
