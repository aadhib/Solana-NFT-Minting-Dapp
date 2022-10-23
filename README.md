# Solana-NFT-Minting-Dapp
NFT minting DApp on Solana Network. This project is made using metaplex and candy machine v2 and has all the basic functionalities such as connect wallet, mint function and view on solscan after the transaction is complete.

This Repository consist of all the files required for the build
- **Hashlips Art Engine** :
This is a program which enables you to create multiple instances of your artwork.
- **Metaplex** :
It is a collection of tools, smart contracts and more designed to make the process of creating and launching NFTs easier.
- **Candy Machine** :
It is a tool that utilizes the metaplex CLI to generate an NFT, link a picture and reelevent meta-data to the NFT token and sale.
- **Arweave** : 
It is a new type of technology that uses a form of data base to store data that cannot be deleted or changed, and uses economics to incentive people to store the data for long periods of time for the first time ever. This combination makes either public or private data permanent.

If you want to download those files seperately clone these repositories :
- Hashlips Art engine
```
git clone https://github.com/HashLips/hashlips_art_engine.git
```
- Metaplex
```
git clone https://github.com/metaplex-foundation/metaplex.git
``` 
- Candy Machine v2
```
git clone https://github.com/exiled-apes/candy-machine-mint.git
```

Tools Required
- git
```
sudo dnf install git-all
```
- node
```
brew install node
```
- yarn
```
brew install yarn
```
- ts-node
```
npm install -g typescript
npm install -g ts-node
```

- Solana Tool Suite
```
sh -c "$(curl -sSfL https://release.solana.com/v1.10.8/install)"
Please update your PATH environment variable to include the solana programs
```

Verify Install :

```
git version 
output : git version 2.32.0 (Apple Git-132)

node --version
output : v16.15.0

yarn --version
output : 1.22.18

ts-node --version
output: v10.7.0

solana --version
output: solana-cli 1.10.11
```

If you are using apple silicon chip you will have to install some additional dependencies
run:
```
brew install pkg-config cairo pango libpng jpeg giflib librsvg
```
---
## **HASHLIPS ART ENGINE**

See Hashlips Art Engine repository for detailed documentation: https://github.com/HashLips/hashlips_art_engine.git

or

Watch This video online for better understanding :
https://www.youtube.com/watch?v=HGx052UU8A0



Example of generated artwork :

![NFT](https://user-images.githubusercontent.com/6594638/166630823-853ed4f2-181a-45eb-9ff6-72ea4862426b.gif)

---

## **METAPLEX**
Installing Metaplex : 
```
git clone https://github.com/metaplex-foundation/metaplex.git ~/metaplex
yarn install --cwd ~/metaplex/js/
```
To check if the install went correctly : 
```
ts-node ~/metaplex/js/packages/cli/src/candy-machine-v2-cli.ts --version
```
---
## **SOLANA SETUP**

Check wallet address :
```
solana address
output:5sfDL785gqrnkjVUBCXkqAtsa8tZKmLKv36q93BeXXXX
```

check balance :
```
solana balance
output: 0 SOL
```

### Solana Devnet Wallet Setup

Create a new wallet :
```
solana-keygen new --outfile ~/.config/solana/devnet.json
output:
Generating a new keypair

For added security, enter a BIP39 passphrase

NOTE! This passphrase improves security of the recovery seed phrase NOT the
keypair file itself, which is stored as insecure plain text

BIP39 Passphrase (empty for none): << enter passphrase Here>> 

Wrote new keypair to /Users/aadhib/.config/solana/devnet.json
=======================================================================
pubkey: 6j5nNrozTJkk1zatiXHezSLZArnRUq3WkGKHACTXXX
=======================================================================
Save this seed phrase and your BIP39 passphrase to recover your new keypair:
## REDACTED ##
=======================================================================
```

Create a File **important** in root directory and save the output from your console.

To make the above generated keypair your default :
```
solana config set --keypair ~/.config/solana/devnet.json
```

Config network to devnet :
```
solana config set --url https://metaplex.devnet.rpcpool.com/
```
To see if everything went well :
```
solana config get
output:
Config File: ~/.config/solana/cli/config.yml
RPC URL: https://metaplex.devnet.rpcpool.com/
WebSocket URL: wss://metaplex.devnet.rpcpool.com/ (computed)
Keypair Path: ~/.config/solana/devnet.json
Commitment: confirmed
```
To add dev Solana (not real one) for deploying and testing purposes :
```
solana airdrop 2
output:
Requesting airdrop of 2 SOL

Signature: 41ZEZqpyNMLUy3kQahWSy349PeDz3Q82dNDHKiA7QcsrAzHs3f7YiDEZWjnFi434DoiiDiDkazkBRycRnctx1m6e

2 SOL
```

Check your balance again :
```
solana balance
output: 2 SOL
```
---

## **CONFIGURING YOUR NFT**

See metaplex docs for more details and options :
https://docs.metaplex.com/candy-machine-v2/configuration

The configuration I have gone with is simple with just the price, total number of NFT's and the date and time the collection goes live 

Here's how it looks :
``` json
{
  "price": 0.013,
  "number": 30,
  "gatekeeper": {
    "gatekeeperNetwork": "ignREusXmGrscGNUesoU9mxfds9AiYTezUKex2PsZV6",
    "expireOnUse": true
  },
  "solTreasuryAccount": "Bo7rAbcBuTy8GykecgRkEYryhaVXsCscmxevUR2LtET1",
  "splTokenAccount": null,
  "splToken": null,
  "goLiveDate": "29 Apr 2022 08:30:00 IST",
  "endSettings": null,
  "whitelistMintSettings": null,
  "hiddenSettings": null,
  "storage": "arweave",
  "ipfsInfuraProjectId": null,
  "ipfsInfuraSecret": null,
  "awsS3Bucket": null,
  "nftStorageKey": null,
  "noRetainAuthority": false,
  "noMutable": false
}
```
