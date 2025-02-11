---
date: 2022-04-17
categories: Flash loan attack
title: Beanstalk Farms Lost $182 Million Due To The Governance Mechanism
---

## Summary

On April 17, 2022, Beanstalk Farms, a DeFi credit-based algorithmic stablecoin protocol built on Ethereum that allows users to earn yield on their cryptocurrency deposits, was targeted in a flash loan attack that resulted in the loss of $182 million, including approximately $77 million in non-Beanstalk assets stolen from liquidity pools. [The exploiter ran off with 24,840 ETH](https://medium.com/@nvy_0x/the-beanstalk-bean-exploit-b038f4d324ea) in profit — approximately $80 million, [the remaining $106 million was flash loaned back to Aave](https://medium.com/coinmonks/beanstalk-exploit-a-simplified-post-mortem-analysis-92e6cdb17ace). The attacker exploited the project's governance mechanism by using a flash loan to gain voting rights, allowing them to transfer the project's funds to their own wallet. The stolen assets were then converted to Ethereum and laundered through Tornado Cash. [The attacker sent $250,000 to the Ukrainian relief fund Ukraine Crypto Donation](https://www.certik.com/resources/blog/6HaLMGIL5sI2fpfEZc0nzS-revisiting-beanstalk-farms-exploit), showcasing their movement of stolen funds. The attack has caused the value of the BEAN stablecoin to drop by approximately 88%, to around $0.12 per tokens. 

## Attackers

The attackers remain unidentified. The hacker's address: [0x1c5dCdd006EA78a7E4783f9e6021C32935a10fb4](https://etherscan.io/address/0x1c5dcdd006ea78a7e4783f9e6021c32935a10fb4). This address is now tagged as "Beanstalk Flashloan Exploiter".

## Losses

Breakdown of the lost $182 million:
* [36 million BEAN](https://twitter.com/peckshield/status/1515680335769456640) ($36 million).
* $33 million in ETH and $32m in BEAN from ETH-BEAN UNI v2 LP tokens ($65 million).
* [79.2 million BEAN3CRV-f Curve LP tokens](https://medium.com/coinmonks/beanstalk-exploit-a-simplified-post-mortem-analysis-92e6cdb17ace) ($79.2 million).
* [1.6 million BEAN-LUSD Curve LP tokens](https://medium.com/coinmonks/beanstalk-exploit-a-simplified-post-mortem-analysis-92e6cdb17ace) ($1.6 million).

## Timeline:

- **April 16, 2022, 08:38 AM:** The attacker deposited some BEAN token to Beanstalk for creating a malicious proposal "InitBip18". The proposal was used for transferring asset to the attacker and took 24 hour to proceed.
- **April 17, 2022, 12:24 PM:** The exploiter launched the attack to execute BIP18.
- **April 17, 2022, 3:24 PM:** [24849.1 ETH ($76,424,649.505) were transferred out to Tornado cash](https://www.certik.com/resources/blog/6HaLMGIL5sI2fpfEZc0nzS-revisiting-beanstalk-farms-exploit) (9 ETH may belong to the attacker).
- **April 17, 2022, 6:41 PM:** The attack was spotted by blockchain analytics company PeckShield. They posted a tweet with the malicious transaction.
- **April 17, 2022, 8:36 PM:** Beanstalk Farms confirmed the attack in Twitter. The Beanstalk team took action to temporarily shut off protocol governance and pause Beanstalk.
- **April 19, 2022, 2:45 AM:** Beanstalk offered 10% of the stolen amount as "whitehat bounty" if the hacker returns 90% to Beanstalk Farms' wallet.
- **August 6, 2022:** [Beanstalk has unpaused and relaunched its protocol during its one year anniversary](https://bean.money/blog/beanstalk-one-year-anniversary) on the Ethereum mainnet.

## Security Failure Causes

The cause of the hack was a security flaw in the governance design of the protocol. [The attacker used a flash loan obtained through Aave to borrow nearly $1 billion](https://etherscan.io/tx/0xcd314668aaa9bbfebaf1a0bd2b6553d01dd58899c508d4729fa7311dc5d33ad7) in cryptocurrency assets, gaining a 67% voting stake in Beanstalk. With this supermajority, they approved the execution of code that transferred the assets to their own wallet. The attack took advantage of the emergencyCommit() function, which allowed immediate execution of a proposal with a 2/3 majority vote, bypassing the protocol's safeguards.