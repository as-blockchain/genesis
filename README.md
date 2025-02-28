# Genesis
genesis block for the as-coin
= genesis.json

# Geth
Go-ETHereum : Official client of ethereum

https://github.com/ethereum/go-ethereum

## Install
https://github.com/ethereum/go-ethereum/wiki/Building-Ethereum


# Instruction

## Remove old data
### !! DANGER !! 

you'll lose all the data you have if you have a ethereum account.

* Mac: ~/Library/Ethereum
* Linux: ~/.ethereum
* Windows: %APPDATA%\Ethereum

```
$ rm -rf ~/.ethereum

$ rm -rf ~/Library/Ethereum

$ rm -rf %APPDATA%\Ethereum
```


## Safe way
```
$ geth removedb
INFO [05-07|15:12:27.396] Maximum peer count                       ETH=50 LES=0 total=50
Remove full node state database (/Users/matthew/Library/Ethereum/geth/chaindata)? [y/n] y
INFO [05-07|15:12:38.190] Database successfully deleted            path=/Users/matthew/Library/Ethereum/geth/chaindata elapsed=1.122ms
Remove full node ancient database (/Users/matthew/Library/Ethereum/geth/chaindata/ancient)? [y/n] y
INFO [05-07|15:12:38.539] Database successfully deleted            path=/Users/matthew/Library/Ethereum/geth/chaindata/ancient elapsed=1.173ms
Remove light node database (/Users/matthew/Library/Ethereum/geth/lightchaindata)? [y/n] y
INFO [05-07|15:12:38.854] Database successfully deleted            path=/Users/matthew/Library/Ethereum/geth/lightchaindata elapsed=625.383µs

```

## boot node
we are not using boot node!

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
INFO [05-07|15:14:19.208] Maximum peer count                       ETH=50 LES=0 total=50
INFO [05-07|15:14:19.220] Allocated cache and file handles         database=/Users/matthew/Library/Ethereum/geth/chaindata cache=16.00MiB handles=16
INFO [05-07|15:14:19.256] Writing custom genesis block 
INFO [05-07|15:14:19.260] Persisted trie from memory database      nodes=3 size=421.00B time=3.519226ms gcnodes=0 gcsize=0.00B gctime=0s livenodes=1 livesize=0.00B
INFO [05-07|15:14:19.260] Successfully wrote genesis state         database=chaindata hash=3b239f…b14e38
INFO [05-07|15:14:19.260] Allocated cache and file handles         database=/Users/matthew/Library/Ethereum/geth/lightchaindata cache=16.00MiB handles=16
INFO [05-07|15:14:19.289] Writing custom genesis block 
INFO [05-07|15:14:19.297] Persisted trie from memory database      nodes=3 size=421.00B time=7.704739ms gcnodes=0 gcsize=0.00B gctime=0s livenodes=1 livesize=0.00B
INFO [05-07|15:14:19.297] Successfully wrote genesis state         database=lightchaindata hash=3b239f…b14e38
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
```

### with RPC
```
$ geth --nat extip:<your_IP> --rpc --rpcaddr "0.0.0.0" --rpcport 8545 --rpccorsdomain "*" --rpcapi "db,eth,net,web3,personal,mine" --nodiscover console
```

```
> admin.addPeer("enode://deb1935c393f8b25c3f521f7facdb1bb2c74d615fa13ac593ba72b2dcefa8783d8589d3e4350bdb30728486f309cccaf56e0cd2391a1f99ff45618a056627593@172.16.0.48:30303?discport=0")
true

> admin.addPeer("enode://ac29e4876c0f452b364a2da2aea52b6ea06d379e080e71cb2e98a6fc27379df2ab66c0b4972f026c7f34396584b112c966567d40512e7fb9c6d7fbf262afedaf@172.16.0.54:30303?discport=0")
true
```

# Console commands

## check the balance
```
> eth.accounts[0]
["0xa20c8b9c59cae6fbb5789d66679af20522d7221e"]
```

```
> eth.getBalance(eth.accounts[0])
1.00000000000008e+32

or

> eth.getBalance("0xa20c8b9c59cae6fbb5789d66679af20522d7221e")
1.00000000000008e+32
> eth.getBalance("0x372b51B29E3CE4Bf18cC871Ee047C45ea64D57dC")
1.00000000000008e+32
```

## convert unit
```
> web3.toWei(1, "ether")
"1000000000000000000"

> web3.fromWei(1, "ether")
"0.000000000000000001"
```

## check the block number
```
> eth.blockNumber
<some number around 10>
```

## check the peers
```
> admin.peers
```

# Mining
## set etherbase
```
> miner.setEtherbase("0xa8e6800fcDA89C0e1Aa79bF5D0596581033Fbb32")
true
```

## start to mining (!! DON'T DO IT !!)
```
> miner.start()
```

## Send money!
### unlock the wallet
```
> personal.unlockAccount(address)
Unlock account 0xa20c8b9c59cae6fbb5789d66679af20522d7221e
Passphrase: 
true
```

### signing test
```
> eth.signTransaction({
    from: "0xa20c8b9c59cae6fbb5789d66679af20522d7221e",
    gasPrice: "20000000000",
    gas: "21000",
    to: '0x3535353535353535353535353535353535353535',
    value: "1000000000000000000",
    data: "",
    nonce: 1
});
```

### Send!
```
> eth.sendTransaction({
    from: '0xa20c8b9c59cae6fbb5789d66679af20522d7221e',
    to: '0x372b51B29E3CE4Bf18cC871Ee047C45ea64D57dC',
    value: '1000000000000000'
})
INFO [05-07|14:53:19.145] Setting new local account                address=0xa20C8B9C59CAe6FBB5789D66679AF20522d7221E
INFO [05-07|14:53:19.146] Submitted transaction                    fullhash=0x16a9260203f3b8d351eac37b5f495e158809c6723ae6982d6bedfdaa068f5880 recipient=0x372b51B29E3CE4Bf18cC871Ee047C45ea64D57dC
"0x16a9260203f3b8d351eac37b5f495e158809c6723ae6982d6bedfdaa068f5880"
```

# Next

https://web3js.readthedocs.io/en/v1.2.0/index.html

https://solidity.readthedocs.io/en/v0.6.7/


# utils

https://ethgasstation.info/

https://faucet.metamask.io/