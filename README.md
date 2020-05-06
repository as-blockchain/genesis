# genesis
genesis block for the as-cin

# Instruction
!! DANGER !!
```
rm -rf ~/.ethereum
```

```
enode://88b75f9b38c4ead46e40b0108b911ecd7ce0337eb731a00b992d85ac92f033cfecba90f9d62155ad622754bf50b7f9243145374f0a68bf923072365a91175993@172.16.0.48:0?discport=30301
```

if you use a docker image
```
$ docker run -p 30303:30303 -p 8545:8545 -v ~/:/root -it /bin/bash
```

```
$ ethereum/client-go account new
```

```
$ ethereum/client-go account list
```

```
$ ethereum/client-go account update a94f5374fce5edbc8e2a8697c15331677e6ebf0b
```

```
$ ethereum/client-go init /root/genesis.json
```

```
$ ethereum/client-go --networkid 1004 --rpc --rpcaddr "0.0.0.0" --rpcport 8545 --rpccorsdomain "*" --rpcapi "db,eth,net,web3,personal,mine" --nodiscover -v ~/:/root console
```

```
$ ethereum/client-go console
```

```
> eth.getBalance("0x68F873F4d77dF1bF8d8e4ab5dCFAb277422be896")
```

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
}```