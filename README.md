# Genesis
genesis block for the as-cin
= genesis.json

# Geth
Go-ETHereum : Official client of ethereum

https://github.com/ethereum/go-ethereum

## Install
https://github.com/ethereum/go-ethereum/wiki/Building-Ethereum


# Instruction
## !! DANGER !! 

you'll lose all the data you have if you have a ethereum account.

* Mac: ~/Library/Ethereum
* Linux: ~/.ethereum
* Windows: %APPDATA%\Ethereum

```
$ rm -rf ~/.ethereum

$ rm -rf ~/Library/Ethereum

$ rm -rf %APPDATA%\Ethereum
```

## boot node
```
enode://88b75f9b38c4ead46e40b0108b911ecd7ce0337eb731a00b992d85ac92f033cfecba90f9d62155ad622754bf50b7f9243145374f0a68bf923072365a91175993@172.16.0.48:0?discport=30301
```

## create account (optional)

```
$ geth account new
```

```
$ geth account list
```

```
$ geth account update a94f5374fce5edbc8e2a8697c15331677e6ebf0b
```

### inside the keystore 
```
{
    "address": "8f0b1f309d68407aa09da69f43def2067a305723",
    "crypto": {
        "cipher": "aes-128-ctr",
        "ciphertext": "355895edd9695e6a886e3a30eafc170d556ae4d866aa96704891ade05d2774ee",
        "cipherparams": {
            "iv": "169c8460b14e00df7b1d7241dd6d96be"
        },
        "kdf": "scrypt",
        "kdfparams": {
            "dklen": 32,
            "n": 262144,
            "p": 1,
            "r": 8,
            "salt": "4a6c4945f727378f3ba44e562a30a5bb30d070e0147599c6be2282d70480fb8c"
        },
        "mac": "0984371067f4df0dfc6473a1aa136c715fced1ffe757efe659d2f3ca16f747b9"
    },
    "id": "882317fd-3a5b-4867-b867-75cbc6b6f54d",
    "version": 3
}
```

## init chain with genesis block
```
$ geth init /root/genesis.json
```

### directory structure

```
/Ethereum/geth/chaindata:
000001.log
CURRENT
LOCK
LOG
MANIFEST-000000

/Ethereum/geth/lightchaindata:
000001.log
CURRENT
LOCK
LOG
MANIFEST-000000

/Ethereum/keystore:
UTC--2020-05-07T02-54-23.615577000Z--ebb2ec712929cbd81b0c640ecc2c7d960f6d5b80
```


## Start console
```
$ geth --nat extip:<your_IP> --nodiscover console 
$ geth --nat extip:<your_IP> --rpc --rpcaddr "0.0.0.0" --rpcport 8545 --rpccorsdomain "*" --rpcapi "db,eth,net,web3,personal,mine" --nodiscover console
```

```
> admin.addPeer("enode://deb1935c393f8b25c3f521f7facdb1bb2c74d615fa13ac593ba72b2dcefa8783d8589d3e4350bdb30728486f309cccaf56e0cd2391a1f99ff45618a056627593@172.15.0.48:30303?discport=0")
> admin.addPeer("enode://ac29e4876c0f452b364a2da2aea52b6ea06d379e080e71cb2e98a6fc27379df2ab66c0b4972f026c7f34396584b112c966567d40512e7fb9c6d7fbf262afedaf@172.16.0.54:30303?discport=0")
```

# Console commands

## check the balance
```
> eth.getBalance("0xa8e6800fcDA89C0e1Aa79bF5D0596581033Fbb32")
```

## check the peers
```
> admin.peers
```

# Mining
## set etherbase
```
> miner.setEtherbase("0xa8e6800fcDA89C0e1Aa79bF5D0596581033Fbb32")
```

## start to mining (!! DON'T DO IT !!)
```
> miner.start()
```