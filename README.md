# Polarizer.json 🕶
Polarizer is a JSON-formatted registry file that enables someone to describe NFTs within a given wallet that should and should not be displayed.

## Why is this needed?
Anyone can deposit NFTs into any other wallet, without requiring anyone's permission to do so. As a result, a wallet may contain some NFTs that its owner may not want to showcase. With open ledgers, it's possible for a website to view and showcase all NFTs owned by a given wallet. While some websites may have built-in ways to hide specific assets, there needs to be an open standard that websites can adopt which instructs front-ends on which NFTs should or should not be displayed.

Some additional reasons include:
- It may be costly to try and send away undesireable NFTs
- Some NFTs may be hard coded as "non-transferrable" meaning they can't be sent away at all

## How does Polarizer work?
Polarizer is a simple `.json` file that defines which NFTs, and NFT contracts should be allowed or disallowed from display. Here is its basic formatting:

```
{
  "name": "Polarizer.json",
  "version": 0.1,
  "allowed": [
  ],
  "blocked": [
  ]
}
```

- `version`: This indicates which version of the Polarizer format is in use
- `allowed`: An array of addresses that refer to individual NFTs, or NFT contract that should be displayed. Note that if *any* address is present in allowed, only those addresses should be displayed
- `blocked`: An array of NFTs or contracts that should not be displayed.

## Example:

```
{
  "name": "Polarizer.json",
  "version": 0.1,
  "allowed": [
  ],
  "blocked": [
    0x6c94954d0b265f657a4a1b35dfaa8b73d1a3f199
  ]
}
```
[View an example here](https://gateway.pinata.cloud/ipfs/QmRXZo6nojy9AwYQ82iUKwJdhTTea1uequBEQEms4xHmEq), as published on IPFS.

In the above example, all NFTs contained within the wallet would be displayed *except* the ones in the blocked array. The address listed in this example is a token contract, meaning that *all* NFTs minted via that contract would not be displayed.

## Where is a polarizer.json file stored?
It can be stored anywhere, really. A useful choice might be IPFS. In practice, perhaps it could be referred to in the corresponding ENS domain for a given wallet address.

## How can websites support Polarizer?
Let's figure it out! All a website would need to do is read a given wallet's polarizer.json file, but we need to come up with a standard set of locations for the website to check against.

## Why is it called Polarizer?
"Polarizer" refers to [polarization](https://en.wikipedia.org/wiki/Polarization_(waves)), which is a technique used in sunglasses and other applications to permit certain waves of light, but not others.
