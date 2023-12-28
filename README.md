# solana-quick-start
Getting started with solana, simple JS scripts

This quick starter has been created thanks to [spl.solana.com/token](https://spl.solana.com/token) and [docs.solana.com/developing/clients/javascript-api](https://docs.solana.com/developing/clients/javascript-api)

## Pre-requisite
- Recent NodeJS version
- Creating dedicated directory ```mkdir solana-poc && cd solana-poc && npm init -y && code .```

## Install Solana Web3 libs
```
npm i @solana/web3.js @solana/spl-token
```

## Get Mint Info

### Create getMint.js
```
const web3 = require('@solana/web3.js');
const splToken = require('@solana/spl-token');

async function getMintInfo(tokenAddress) {
    const connection = new web3.Connection(web3.clusterApiUrl('mainnet-beta'));
    const mintPublicKey = new web3.PublicKey(tokenAddress);
    try {
        const mintInfo = await splToken.getMint(connection, mintPublicKey);
        console.log(mintInfo);
    } catch (error) {
        console.error("Erreur while retrieving mint info:", error);
    }
}

// Change token address below
const tokenAddress = 'yourTokenAddressHere';
getMintInfo(tokenAddress);
```

### Start getMint.js
```
node getMint.js
```
