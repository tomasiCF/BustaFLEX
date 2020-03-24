# BustaFLEX


## General BCH Functions

- [create-wallet](https://github.com/tomasiCF/slp-sdk/blob/master/examples/create-wallet) Create a SLP compatible HD Node wallet on
  the BCH mainnet. Send a small amount of BCH (0.0001 or more) to the address
  saved in the `wallet.json` file generated by this app. All other example apps
  read this `wallet.json` file.

- [check-token-balance](https://github.com/tomasiCF/slp-sdk/blob/master/examples/check-token-balance) Check the token balance of your
BCH wallet for a single tokenId

- [check-balances](https://github.com/tomasiCF/slp-sdk/blob/master/examples/check-balances) Check the balance of your BCH wallet. This
  displays both BCH information as well as SLP token information.

## SLP Token Functions

- [create-token](https://github.com/tomasiCF/slp-sdk/blob/master/examples/create-token) - Create a new SLP token class. Run the
  [create-wallet](https://github.com/tomasiCF/slp-sdk/blob/master/examples/create-wallet/) example first, and fund your wallet with a few
  cents of BCH first.

- [create-nft](https://github.com/tomasiCF/slp-sdk/blob/master/examples/create-token) - Create a new SLP
[non-fungible token](https://coincentral.com/nfts-non-fungible-tokens/). Run the
[create-wallet](https://github.com/tomasiCF/slp-sdk/blob/master/examples/create-wallet) example first, and fund your wallet with a few
cents of BCH first.

- [mint-token](https://github.com/tomasiCF/slp-sdk/blob/master/examples/mint-token) - Mint additional SLP tokens for an existing class
  controlled by your wallet.

- [send-token](https://github.com/tomasiCF/slp-sdk/blob/master/examples/send-token/) - Send tokens from your address to another address.

- [burn-all](https://github.com/tomasiCF/slp-sdk/blob/master/examples/burn) - Burn all tokens for an address by tokenId.

- [lookup-token](https://github.com/tomasiCF/slp-sdk/blob/master/examples/lookup-token) - Lookup token information based on the token `id`.

- [list-all-tokens](https://github.com/tomasiCF/slp-sdk/blob/master/examples/list-all-tokens) - List every token in existence.

- [conversion](https://github.com/tomasiCF/slp-sdk/blob/master/examples/conversion) - Convert between address formats.


## [derviation path](https://github.com/tomasiCF/BustaFLEX/blob/master/derviationPath.md)

### Background

Derivation paths are related to HD Wallets or HD Keys, a type of wallet where you have a single, human readable, seed phrase that unlocks a number of accounts / addresses / private keys across any supported network. These phrases typically look like “brain surround have swap horror body response double fire dumb bring hazard”

The technical specification for the most commonly used HD wallets are...

    BIP-32 - HD wallets specification
    BIP-39 - the mnemonic phrase / word list / etc. piece of this puzzle.
    BIP-44 - the derivation path stuff / algorithms.


### about "derviation path"
It's the

   XYZ + 😺 + ABC + & + 1

part of it.

The actual derivation path pieces

Full path: m/44'/145'/0'/0 （Use this for FLEX）

What each number represents: m / purpose' / coin_type' / account' / change / address_index

    m/

Probably just a random way to start a string so that coders can easily tell if something is a derivation path, not you starting to type "mommy".

    44' (purpose)

This is always 44'. However, if it were decided that there were a better evolution of the HD key system, you could change it to be 45' so that, again, coders could tell the difference between an old system and a new system.

    60' (coin type)

Which blockchain are you accessing? Each blockchain has a number that represents it. Bitcoin is 0. Ethereum is 60. Aion is 425. When you create a new blockchain, you apply for an unused number. You can see all the chains and their numbers here: https://github.com/satoshilabs/slips/blob/master/slip-0044.md

    0' (account)

A number that starts at 0 and increases. A layer of separation or hierarchy. (more on that below)

    0 (change)`

Sometimes used in Ethereum, sometimes not. Was created for Bitcoin originally which doesn't really have "accounts", it has "unspent transaction outputs". Basically you never send a part of your bitcoin holdings around—you send all your bitcoin to multiple addresses. If you have 0.75 BTC but only want to send me 0.5 BTC, you would send me 0.5 BTC and then send yourself 0.25 BTC. "Yourself" could be back to the original address or to another address you have access to (for example, the next address on the "list"). This number says "send whatever I don't want to send to my friend to the 10th address on my list. Or the 0th address on the list (aka the address I am sending from).

    0' (index)

Another variable to get different accounts.

### Seperation and Hierarchy

Some of the variables above are based on external forces, like what chain I am on. Some are chosen by the user or the wallet software, like the change variable. The account and index variables give me (or my wallet) more things to change.

For example, let's say I want to separate my personal FLEX from my company's FLEX. I could use m/44'/145'/0 for the company and m/44'/145'/0'/0'/1 for my personal.

But let's say I want to have different addresses for...

I could use m/44'/145'/0'/0 for savings, m/44'/145'/0'/1 for paychecks, m/44'/145'/0'/2 for getting paid back by my friend, and so forth. I could also do the same with the company accounts. 
