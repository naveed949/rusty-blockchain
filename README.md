# rusty-blockchain
Blockchain implementation in Rust using UTXO model and Proof of Work consensus algorithm.

## How to run
1. Clone the repository
2. Run `cargo build --release` in the root directory
3. Run `./target/release/rusty-blockchain` in the root directory to get usage information

## Usage
```
rusty-blockchain 0.1.0
Blockchain implementation in Rust using UTXO model and Proof of Work consensus algorithm

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

SUBCOMMANDS:
    createblockchain    Create a new blockchain
    createwallet        Create a new wallet
    getbalance          Get the wallet balance of the target address
    help                Prints this message or the help of the given subcommand(s)
    listaddresses       Print local wallet addres
    printchain          Print blockchain all block
    reindexutxo         rebuild UTXO index set
    send                Add new block to chain
    startnode           Start a node

```

## Example
1. Create a new wallet
```
$ ./target/release/rusty-blockchain createwallet
Your new address: 1PwSrPpcVTydmp7KuYPvHmC87ycBG4hAyj
```

2. Create a new blockchain
```
$ ./target/release/rusty-blockchain createblockchain 1PwSrPpcVTydmp7KuYPvHmC87ycBG4hAyj
Mining the block
0017c8fd8a0131ff00d94d3b73f8be4f446bb721b6d922911f90b6628b3eea1b

Done!
```

3. Get the wallet balance of the target address
```
$ ./target/release/rusty-blockchain getbalance 1PwSrPpcVTydmp7KuYPvHmC87ycBG4hAyj
Balance of 1PwSrPpcVTydmp7KuYPvHmC87ycBG4hAyj: 10
```

4. Send coins to another address
```
$ ./target/release/rusty-blockchain send 1PwSrPpcVTydmp7KuYPvHmC87ycBG4hAyj 16A8KdW747ESnCub1QWEMTfgUSLXHHoE9c 100 11PwSrPpcVTydmp7KuYPvHmC87ycBG4hAyj 5
Mining the block
0029c0efe2d9d4b7d7c12d90c7814a65752b55862d42964effa219379f1933a5

Success!
```

5. Print blockchain all block
```
$ ./target/release/rusty-blockchain printchain
Pre block hash: 0017c8fd8a0131ff00d94d3b73f8be4f446bb721b6d922911f90b6628b3eea1b
Cur block hash: 0029c0efe2d9d4b7d7c12d90c7814a65752b55862d42964effa219379f1933a5
Cur block Timestamp: 1717510542527
- Transaction txid_hex: e7e8bba6e49884e1b8ad6ec97c4671db89b986ad4179c31caa942762167c3423
-- Input txid = cc8fd08c709f2004c0fdcaa392e6c1431d1995135eb65afd2db64243d3123014, vout = 0, from = 1PwSrPpcVTydmp7KuYPvHmC87ycBG4hAyj
-- Output value = 10, to = 16A8KdW747ESnCub1QWEMTfgUSLXHHoE9c
- Transaction txid_hex: 6025ceeb938be7ed012b64896e64ffce9f28becc2b0b8563884d3d321cdad69f
-- Output value = 10, to = 1PwSrPpcVTydmp7KuYPvHmC87ycBG4hAyj

Pre block hash: None
Cur block hash: 0017c8fd8a0131ff00d94d3b73f8be4f446bb721b6d922911f90b6628b3eea1b
Cur block Timestamp: 1717508775458
- Transaction txid_hex: cc8fd08c709f2004c0fdcaa392e6c1431d1995135eb65afd2db64243d3123014
-- Output value = 10, to = 1PwSrPpcVTydmp7KuYPvHmC87ycBG4hAyj
```

6. Rebuild UTXO index set
```
$ ./target/release/rusty-blockchain reindexutxo
Done! There are 2 transactions in the UTXO set.
```