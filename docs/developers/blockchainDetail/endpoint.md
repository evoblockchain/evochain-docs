# Endpoint

## Used by
- evochain-java-sdk
- Metamask

## Mainnet JSON-RPC Endpoint (chain-id: evochain-66)
- https://evochainrpc.evoblock.com

## Mainnet Websocket Endpoint
- wss://evochainws.evoblock.com:8443

### How to configure MetaMask with EVO(Mainnet) in one step

```javascript
currentProvider.send({
    "method": "wallet_addEthereumChain",
    "params": [
        {
            "chainId": "0x42",
            "chainName": "EVO Main",
            "rpcUrls": ["https://evochainrpc.evoblock.com/"],
            "nativeCurrency": {
                "name": "EVO",
                "symbol": "EVO",
                "decimals": 18
            },
            "blockExplorerUrls": ["https://www.evoblock.com/evo"]
        }
    ]
})
```

## Testnet JSON-RPC Endpoint (chain-id: evochain-65):
- https://evochaintestrpc.evoblock.com

## Testnet Websocket Endpoint
- wss://evochaintestws.evoblock.com:8443

### How to configure MetaMask with EVO(Testnet) in one step

```javascript
currentProvider.send({
  "method": "wallet_addEthereumChain",
  "params": [
    {
      "chainId": "0x41",
      "chainName": "EVO Testnet",
      "rpcUrls": ["https://evochaintestrpc.evoblock.com"],
      "nativeCurrency": {
        "name": "EVO",
        "symbol": "EVO",
        "decimals": 18
      },
      "blockExplorerUrls": ["https://www.evoblock.com/evo-test"]
    }
  ]
})
```





