# notarization-component

Notarization component is system used to notarize text or files in distributed fashion. It exposes RESTful api for which can take JSON objects / strings as ´application/json´ data or other files as ´multipart/form-data´.

## Environment

This program uses environmental variables for configurations in production. Out of box software works in development mode. In development mode preset enviroment is used.

When in production, following enviromental variables must be set;

```
PORT=[port to listen to]
GETH=[ip:port for ethereum node]
```

## NPM scripts

```
npm start - Starts the application with nodemon and babel
npm run build - Build application for production use
npm run serve - Start the production application
```

## Smart contract setup for development enviroment

Follow this procedure to migrate smart contracts for development environment

1. Go to smart_contract folder
   `cd smart_contract/`
2. Start truffle - This step launches local Ethereum instance
   `truffle develop`
3. In the truffle console, compile the smart contract (creates a build/ folder)
   `compile`
4. In the truffle console, migrate the smart contract to the current instance
   `migrate`

Now you have started a local Ethereum blockchain instance, and other applications can interact with migrated smart contracts

## Encryption

All the files are hosted in IPFS, but as the files are available for everyone with the correct hash, we need to encrypt the files before uploading them. When the file is being fetched back, it'll be decrypted back to it's original form. Encryption is done with RSA key located in ./keys/ folder.

## Http-server

Http-server is used for local file hosting after the file has been fetched from IPFS

1. Install http-server globally
   `npm install http-server -g`
2. Run http-server on port 8080 in the root folder of this app
   `http-server`
