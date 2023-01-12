# FAQ for developers

## how to solve the error of mismatch transaction hash when using `ethers.js`.

### Solution
* install the package of `evochain-etherjs`(which was released by team of evochain ) via npm 
```shell script
sudo npm install evochain-ethers
```
* using `evochain-ethers.js` to instead the original `ethers.js`

### Root cause
The `ethers.js` will generate a transaction hash in local via the algorithm of ethereum that using RLP+KECCAK256, as we know the evochain was based on cosmos-sdk, it use the algorithm of cosmos style to generate a transaction hash(Amino + SHA256), that's a huge inconsistent, it will failed when `ethers.js` try to get result of transaction execution via using the ethereum style hash on evochain

### Additional
1. [Click to get source code of evochain-ethers](https://github.com/evoblockchain/ethers.js/tree/ray)
2. [Click to get example of sending transaction on evochain](https://github.com/evoblockchain/solidity-sample)
