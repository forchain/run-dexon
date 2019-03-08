# Run DEXON

Instructions to run a DEXON block proposer node.

## Generate Node Key

A node key is required to operate a BP node. Run the following command to
generate a node key:

    docker run -v $PWD:/mnt -it dexonfoundation/dexon-tools nodekey generate /mnt/node.key

This show output content similar to the following

    Node Address: 0x93aA8C9C77De627E665F0b4015B7271B9Be89E83
    Public Key: 0x046272a157cbffa00677be00b08c9d47f295539b07e53360754579ad5e933a638ba58dcf850484e7d40b8bc163a920082b2500ee54968db7155c6231c7e4eed592

A file `node.key` can be found under current working directory. `node.key` is
very important as it contains the node private key. Please save this file
securely.

### Genesis BP

If you are a genesis BP, you need to contact your contact at DEXON foundation
and provide the following information:

1. Node Public Key (the public key generated above)
2. Name of the node
3. Contact email
4. Node Location
5. Website URL

### Normal BP

For normal non-genesis BP, you need to call the `stake` method and provide the
same information similar to the genesis BP. After stake is called, you can
start your BP node and start producing blocks.

Note that after staked, the configuration will start to take effect after 2
rounds.


## Running BP node

Use the following command to start the BP node:

    docker run -v $PWD:/mnt -it dexonfoundation/dexon gdex \
        --bp \
        --nodekey=/mnt/node.key \
        --datadir=/mnt/datadir \
        --syncmode=full \
        --cache=1024 \
        --gcmode=archive

Please make sure you have enough diskspace in the current working directory.z
