# Good resources to get a deep understanding
## Referer Books
#### Mastering Ethereum
* https://www.amazon.com.br/Mastering-Ethereum-Andreas-Antonopoulos/dp/1491971940

## Concept websites
* https://swcregistry.io/ (Smart Contract Weakness Classification and Test Cases) [offers a complete and up-to-date catalogue of known smart contract vulnerabilities and anti-patterns along with real-world examples]
* https://consensys.github.io/smart-contract-best-practices/attacks/reentrancy/ (Short version from the above link)
* https://code4rena.com/reports
* https://github.com/ethereumbook/ethereumbook/blob/develop/09smart-contracts-security.asciidoc
* https://github.com/arunimshukla/Best-DeFi-Security-Practices
* https://github.com/immunefi-team/Web3-Security-Library?utm_source=immunefi

## Practical websites
* https://www.damnvulnerabledefi.xyz/
 ```
 Solutions to the above link
 * https://cmichel.io/damn-vulnerable-de-fi-solutions/ (Cmichel - Top Bug hunter on code4rena)
 ```
* https://ethernaut.openzeppelin.com/
 ```
 Solutions to the above link
 * https://cmichel.io/ethernaut-solutions/ (Cmichel - Top Bug hunter on code4rena)
 * https://stermi.medium.com/lets-play-ethernaut-ctf-learning-solidity-security-while-playing-1678bd6db3c4
```
* https://cryptozombies.io/
* https://capturetheether.com/

## Youtube Video and Channel
* https://www.youtube.com/@andyli (Andy Li)
* https://www.youtube.com/watch?v=aX7ye0yyynY (Attacking an Ethereum L2 with Unbridled Optimism @ UCSB CCS W2022)[Jay Freeman]
* https://youtu.be/Fr6b-fjn-zE?t=195 (Top Wardens Cmichel and 0xLeastwood face-off during the C4 Showdown Game Show)

## Keywords

[@cmichelio](https://twitter.com/cmichelio)

Become familiar with the most used smart contracts
There are certain contracts, patterns or even algorithms that you will see over and over again during your auditing career. It’s good to become familiar with them and deeply understand how they work and their nuances.

* Token contracts
```
The most used token standards are EIP20 for fungible tokens, and EIP721 for NFTs. There are many more, but these two are all you need to know in the beginning. It’s important to understand that the original ERC20 standard evolved a lot and there are tokens that do not comply with the final EIP20 (most notably USDT), which does not return a success boolean among other issues. You should also understand that tokens can have different decimals and they’re to be interpreted as a floating-point number with the decimals precision, i.e., 1e18 TOKENS (= 10**18 TOKENS) ~ 1.0 TOKENS for a token with 18 decimals. You’ll encounter a lot of bugs where some computed token amount is in the wrong number of decimals.
```
* Proxies
```
Ethereum contracts are not upgradeable. If you want to update the code, you need to deploy a new contract. However, that means that the storage which still resides in the original contract is also lost. Thus proxies implement the idea to separate the storage from the logic. There are many different proxy implementations, have a look at the OpenZeppelin Proxy. You should understand how delegatecall is essential for building proxies.
```
* MasterChef
```
The MasterChef is a staking contract where users deposit liquidity pool (LP) tokens and receive rewards proportional to their time * stakeAmount. This contract has been forked a lot but the main reason why it’s important to understand is that its reward algorithm appears in many different places. Paradigm calls it the Billion-dollar algorithm. You should understand how it works and why it’s needed in a blockchain setting (cannot update all users at the same time).
```
* Compound
```
I’d say Compound is the basis for all decentralized peer-to-peer lending protocols. You should know it as a lot of DeFi primitives interact with lending protocols in some way. The code is also cleaner than Aave’s and it’s a great example of what good documentation looks like. Its Governor & TimeLock contracts are used as governance contracts of many other protocols as well. You should notice the similarities between the MasterChef reward algorithm and the way debt is accrued for the user through borrowIndex.
```
* UniswapV2
```
While Uniswap is already on V3, Uniswap V2 is significantly simpler, less gas-golfed, and still the basis for understanding automated market makers (AMMs) in general. You should also understand how LP tokens (more generally, share tokens that give you a fair share of an underlying balance) work.
```
