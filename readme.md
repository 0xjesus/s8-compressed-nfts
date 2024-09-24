# Fellowship S8: Minting Compressed NFTs with a Custom Backend

## Introduction

As part of the S8 from Solana's fellowship program, I developed a custom backend to construct transactions for minting compressed NFTs (cNFTs). 
---

## Project Objectives

- **Create a Collection**: Establish a new NFT collection on the Solana blockchain.
- **Build a Merkle Tree**: Implement a Merkle tree structure to manage cNFTs efficiently.
- **Verify the Collection**: Ensure the collection is verified using optimized transactions.
- **Mint cNFTs in Batches**: Overcome transaction size limitations by minting NFTs in smaller groups.
- **Frontend Integration**: Test and interact with the backend through a custom frontend application.

---

## My Learning Journey

### Creating the Collection

I began by setting up a new NFT collection using the Metaplex protocol. Crafting the `createCollection` function was straightforward initially, but integrating it seamlessly with my custom backend required a deeper dive into Metaplex's API.

- **Challenge**: Understanding the nuances of Metaplex's collection creation process.
- **Solution**: Studied Metaplex documentation and examined open-source projects for best practices.
- **Outcome**: Successfully implemented the collection creation function in the [Metaplex service](https://github.com/0xjesus/s6-solana-pay-api/blob/main/services/metaplex.service.js#L122).

### Building the Merkle Tree

Implementing a Merkle tree was essential for efficient cNFT management. This was a new concept for me, and I had to grasp both its theoretical underpinnings and practical applications.

- **Challenge**: Limited prior experience with Merkle trees and their role in blockchain.
- **Solution**: Researched Merkle tree structures and their implementation in blockchain systems.
- **Outcome**: Developed the `createMerkleTree` function in the [NFT service](https://github.com/0xjesus/s6-solana-pay-api/blob/main/services/nft.service.js#L70), enhancing data integrity and verification processes.

### Overcoming Transaction Size Limitations

When I attempted to verify the collection, I encountered an issue: the transaction was too large to process.

- **Challenge**: The collection verification transaction exceeded the size limit imposed by the Solana network.
- **Solution**: Introduced a **Lookup Table** to reduce the transaction size by mapping and reusing frequently accessed addresses.
- **Outcome**: Created the `createLookupTable` function in the [Lookup Table service](https://github.com/0xjesus/s6-solana-pay-api/blob/main/services/cnfts.service.js#L41), which optimized the transaction size.

### Verifying the Collection

With the Lookup Table in place, I proceeded to verify the collection.

- **Challenge**: Ensuring that the optimized transaction correctly verified the collection without any data loss or errors.
- **Solution**: Tested the verification process extensively using different scenarios and data sets.
- **Outcome**: Successfully verified the collection with a smaller, efficient transaction in the [cNFTs service](https://github.com/0xjesus/s6-solana-pay-api/blob/main/services/cnfts.service.js#L225).

### Frontend Integration and Testing

To interact with my backend services, I developed a frontend application.

- **Challenge**: Creating a user-friendly interface that could input data and handle transaction signing.
- **Solution**: Built a web application using Vue.js, focusing on simplicity and functionality.
- **Outcome**: The frontend ([s8.vue](https://github.com/0xjesus/s6-solana-pay/blob/main/pages/s8.vue)) allowed me to test transactions in real-time and ensured seamless integration with the backend.

### Minting cNFTs in Batches

Given the transaction size constraints, I decided to mint cNFTs in batches of three addresses.

- **Challenge**: Managing the batching process and ensuring all NFTs were minted correctly.
- **Solution**: Wrote the `mintCompressedNFTs` function to handle batch minting efficiently.
- **Outcome**: Minted all cNFTs successfully, with each batch processed without errors ([cNFTs service](https://github.com/0xjesus/s6-solana-pay-api/blob/main/services/cnfts.service.js#L108)).

---

## Reflections and Learnings

This project was a significant learning curve. Here are some key takeaways:

- **Deepened Understanding of Blockchain Mechanics**: Implementing Merkle trees and Lookup Tables gave me practical insights into how blockchain systems optimize data storage and transaction efficiency.
- **Problem-Solving Under Constraints**: Facing transaction size limitations forced me to think creatively and find solutions like batching and using Lookup Tables.
- **Full-Stack Development Experience**: Building both the backend and frontend allowed me to see the project from end to end, improving my skills in API development and user interface design.
- **Importance of Testing**: Continuous testing at each stage was crucial. It helped me catch and fix issues early, ensuring the final product was robust.

---

## Project Outcomes

- **Successfully Minted cNFTs**: Minted compressed NFTs for multiple wallets in batches, overcoming size limitations.
- **Verified Collection**: Ensured that the NFT collection was verified and met all necessary criteria on the Solana blockchain.
- **Functional Frontend Application**: Developed a frontend that can input data and sign transactions, enhancing user interaction.

---

## Batch Transactions and Wallets

### Batch 1

- **Wallets**:
  - `7jQFJLS3QRGJyshYkLgp4QQH8D5c9qym2LQzkhag38UD`
  - `8J9Hz2tfFLDhE5vcdbinCMug4xqyBCfQCoi4QYfVapEn`
  - `A1mq3dn2tUBfJB6WjnL4XtVQgGLGAUD3FeiMLuUQoRMu`
- **Transaction**: [View on Solscan](https://solscan.io/tx/2iBvoWnk18wtp8Jd6tp4CPbx5FTCAcGsnM1bjVTnTZmKEKDkTuZYC9wqMzkuJYhFyrt2SvHqZbaycadus8gSj6EZ)

### Batch 2

- **Wallets**:
  - `HjJQdfTHgC3EBX3471w4st8BXbBmtbaMyCAXNgcUb7dq`
  - `BtSTqq27A7xTMaCPWEhNwdf4eHsLWiWZvhQS2ABMd1Y4`
  - `9riZWGcTFTLoBpmRM5xfYXCrHsxoqL4ynqBYtNxskYHV`
- **Transaction**: [View on Solscan](https://solscan.io/tx/4Z2PwiwtLCsHGaFF1JvToLHFZp96cu8vZwyn5W8jGVC96zjMzbASUoVzzhVCvbikvtCVVsdDbyyyLQegzhrmTyAs)

### Batch 3

- **Wallets**:
  - `H3QFot1G5Xe8wAjkQbLLt5dEYsHBsicKLHL1aSBv2H2d`
  - `G1ZRP9Sz87SZJ6ZdsqaK8QxbXGTwCFv1SYnheRtY63DW`
  - `8MgdhXTpfWp5k2m1Q2CxMkETgenkYasNqGW88nUANRkR`
- **Transaction**: [View on Solscan](https://solscan.io/tx/3DKx2qNXKKrzwkWM7CLujVJ71KcjjN6ZpBa2smbQNimKUEWsUVQqU8woxurkHpoC3p8npop2uhrsMAfU37wvXs4R)

### Batch 4

- **Wallets**:
  - `6X4G9p5kiE6tDXkBHfpqispJ2B6YfAA3tBGcKvaXaht2`
  - `8HWXSHAngoGE9dudeZUcvnP7xRr9Wb4gy7H8VS5GRo7N`
  - `9BbWp6tcX9MEGSUEpNXfspYxYsWCxE9FgRkAc3RpftkT`
- **Transaction**: [View on Solscan](https://solscan.io/tx/4gc5e2ui8WMBho5ad314nRUawtAJnKv8z782aWFnUHWJ4xoeipFMMMLyskafogh3d9VLjrQodsqhqe7MNNz7bjcc)

### Batch 5

- **Wallets**:
  - `3dfxtPdadK4CdHC1HjcD6Fc2J3x3REy55RyDxAfYuf1d`
  - `Fhrr8gFyNAASoCM2GprrjaNahgCJyb5SVV6V5oHr72Fj`
  - `DVxLfD4BFF3dLUtpvDZ5jbZExjknE1m2WwH2axz2J6ge`
- **Transaction**: [View on Solscan](https://solscan.io/tx/4Yk4dXTbB82ap4ZkPyxTLhXn1Q2ezpbGj94xGunCn54FErCqD9D2TEnhF2RmnkU6dra3rpV5zKVBedvdmf5u7tjj)

### Batch 6

- **Wallets**:
  - `3o5cfcL9VS31T9N5ZbQgLTHokpxiWbTtjoAMjUp2SNey`
  - `9unenHYtwUowNkWdZmSYTwzGxxdzKVJh7npk6W6uqRF3`
  - `3dTSLCGStegkuoU6dc75DbRdJk4rKV3d5ZCZdSWbTcQv`
- **Transaction**: [View on Solscan](https://solscan.io/tx/5c2xxHvfjPUd3875wbaBSfJXurGvBbwdBjJRrp13ucaqmWpXkZuR85n2VnNiSAjhDEtupsGzGvQm2fFbPsC4G4jj)

### Batch 7

- **Wallets**:
  - `6ggGtCSpE6moyjDhQQ7MfQ8cw89DcgtYJhaKZaKJ59CQ`
  - `9riZWGcTFTLoBpmRM5xfYXCrHsxoqL4ynqBYtNxskYHV`
  - `JCsFjtj6tem9Dv83Ks4HxsL7p8GhdLtokveqW7uWjGyi`
- **Transaction**: [View on Solscan](https://solscan.io/tx/4FkXMQPHKxKjnak27H2jaTqhHqfQ35xTk9MWiV4jyxqq7VsBQmN28tod7xPcUKvL4Vq82PTMzWUWWQARdivpe4oS)

### Batch 8

- **Wallets**:
  - `DH9oe9rfZWkRfBVWvib11ihrgCaYP1jGrD9fXcvhun37`
  - `7jQFJLS3QRGJyshYkLgp4QQH8D5c9qym2LQzkhag38UD`
  - `HdaKENyK8fxod85QipFYZffC82PmsM8XEW4prcZbeQiK`
- **Transaction**: [View on Solscan](https://solscan.io/tx/57hrk8b24NVAgauyt2M9cHomzjsGd74Tgw83G7Tg3m4jWJawRq1stw3hv6yEFnagjz4ajEALTTNZWsCaDMu9JAr1)

### Batch 9

- **Wallets**:
  - `EcrHvqa5Vh4NhR3bitRZVrdcUGr1Z3o6bXHz7xgBU2FB`
  - `GyETGp22PjuTTiQJQ2P9oAe7oioFjJ7tbTBr1qiXZoa8`
  - `frae7AtwagcebTnNNFaobGH2haFUGNpFniKELbuBi2z`
- **Transaction**: [View on Solscan](https://solscan.io/tx/z4egcxLJNP42qYujRGaaFuN2zLpLX3TyErf5pXrzAjHgHyXyfxrk3C4UWKYxYN2LkonNazEVRJA9LZ89HwTGXA9)

### Batch 10

- **Wallets**:
  - `38rc27bLd73QUDKmiDBQjsmbXpxinx8metaPFsRPSCWi`
  - `4syk2oXfU7kgpAPAxsyBv47FHeNuVz5WGc2x8atGNDd2`
  - `HFJEhqTUPKKWvhwVeQS5qjSP373kMUFpNuiqMMyXZ2Gr`
- **Transaction**: [View on Solscan](https://solscan.io/tx/5TyX14Y18AcqXMVDPwxk8NYbQCdJ3jGpMWFKt3M2q9ntJf1Car8jzujBMN87AWjubDV6w3jitZp1TfT3i2jAFCpK)

### Batch 11

- **Wallets**:
  - `72hBoHW3TDBHH8vASheaqwVAb8ez3SJAhwtegN5UQvJ9`
  - `CxjawXnJxAyb7Zx3xCkSD3nxamdpcfSikvnnC7C8RMHh`
  - `A1mq3dn2tUBfJB6WjnL4XtVQgGLGAUD3FeiMLuUQoRMu`
- **Transaction**: [View on Solscan](https://solscan.io/tx/5Us9D8kECm7JpFE6XfsJ3skgahxZJxFvzUJzQ4HuZEKPYPz2hkEUAR4YmhcnBVpMfqeA6h9ZqhP7SdRdNQdqxr8y)

### Batch 12

- **Wallets**:
  - `2hNdA3G3hfwUN6z28mgFTAjmkXdTvHsRiTXQP3AZjaij`
  - `ji1E9W3P4Yesmwcv6m5rgBs6dGnshaTcfaFoRW6qcjL`
  - `HT8DNntQe2ZN1v763zUqPou5wwNGTg6xBPCDg31vhjrv`
- **Transaction**: [View on Solscan](https://solscan.io/tx/4NbHEkKCb9bDHAB6McgLU1ZQsjMBKMDv2g1NexGztrUttQbrteLdk5FyB5aiN5t6KCbzuvtHjnnYga3Q9eHPetBq)

### Batch 13

- **Wallets**:
  - `BsdgGRzDmVTM8FBepRXrQixMZgjP6smsSbuDb1Y7VJB6`
- **Transaction**: [View on Solscan](https://solscan.io/tx/2WY6ujdbZrgXgaR5KvHgvecrXyhjZMbmnFZxyfKJ6inCPtqbjpPU1hKBdYDkSmJJMeFJ36eR6VJYU4Jkq87wiaYM)

---

## Wallet to NFT Mapping

| Wallet ID                                   | NFT Link                                                                                      |
|---------------------------------------------|-----------------------------------------------------------------------------------------------|
| 7jQFJLS3QRGJyshYkLgp4QQH8D5c9qym2LQzkhag38UD | [NFT 1](https://solscan.io/token/5nPFuys5RrPkyjawSw9jm9DMh4AZVwhoGhYQH4PBd54c)           |
| 8J9Hz2tfFLDhE5vcdbinCMug4xqyBCfQCoi4QYfVapEn | [NFT 2](https://solscan.io/token/ef4eHCS2umqrLRjzEojniLGzWXNUwKamtNZVt13KdqN)           |
| A1mq3dn2tUBfJB6WjnL4XtVQgGLGAUD3FeiMLuUQoRMu | [NFT 3](https://solscan.io/token/FZAS3wxYJScg7W28g6piGam2mEWNQw7Wciv1EifByYbj)           |
| HjJQdfTHgC3EBX3471w4st8BXbBmtbaMyCAXNgcUb7dq | [NFT 4](https://solscan.io/token/AkP23zFHfP1qWBwP8LuVEU3pt83F9Z4RYgEtrw3JALqw)           |
| BtSTqq27A7xTMaCPWEhNwdf4eHsLWiWZvhQS2ABMd1Y4 | [NFT 5](https://solscan.io/token/DwkB8ta517cvRa74FSTmErTTZmGThkKhG3ZJYpku7vzV)           |
| 9riZWGcTFTLoBpmRM5xfYXCrHsxoqL4ynqBYtNxskYHV | [NFT 6](https://solscan.io/token/AdjrrHHxet5HPNWZ7wNGHKTWKLnKqiNPaqFLsno51ZSk)           |
| H3QFot1G5Xe8wAjkQbLLt5dEYsHBsicKLHL1aSBv2H2d | [NFT 7](https://solscan.io/token/3ow2ri8cG3DSYjrz9oN7cCR6in4GV3tJgWugBmMbJBx9)           |
| G1ZRP9Sz87SZJ6ZdsqaK8QxbXGTwCFv1SYnheRtY63DW | [NFT 8](https://solscan.io/token/GHUBJ3sKdtnrkNQDpy482ae4KyWBuscriDXxr8mS3nxF)           |
| 8MgdhXTpfWp5k2m1Q2CxMkETgenkYasNqGW88nUANRkR | [NFT 9](https://solscan.io/token/7U5FrDRDPc9Eo7i1FSFPVJoMQnLRL37pSg5qUUoptzdi)           |
| 6X4G9p5kiE6tDXkBHfpqispJ2B6YfAA3tBGcKvaXaht2 | [NFT 10](https://solscan.io/token/E6LkhWvoxAR8wNLh3xWjvU6gwqy86fJJrF6aVNgJ5Hby)         |
| 8HWXSHAngoGE9dudeZUcvnP7xRr9Wb4gy7H8VS5GRo7N | [NFT 11](https://solscan.io/token/GY2iy1bQTbv6wTBEXPk58v9U6dU5XMFxCpmr4tmRxDcE)         |
| 9BbWp6tcX9MEGSUEpNXfspYxYsWCxE9FgRkAc3RpftkT | [NFT 12](https://solscan.io/token/Lz4SS6ADcoybc7HiEfDoQ4VQrE1ove6C3t2LzeVqrnW)           |
| 3dfxtPdadK4CdHC1HjcD6Fc2J3x3REy55RyDxAfYuf1d | [NFT 13](https://solscan.io/token/3oJhQy9r4FpFxM4FsRwdMKca7fmFtrmNkuVDbfnkSNPd)          |
| Fhrr8gFyNAASoCM2GprrjaNahgCJyb5SVV6V5oHr72Fj | [NFT 14](https://solscan.io/token/GESG4xa8eQwQeXLrfFFsQ1x85JkPtHtqPDrtyhx1FR56)          |
| DVxLfD4BFF3dLUtpvDZ5jbZExjknE1m2WwH2axz2J6ge | [NFT 15](https://solscan.io/token/9n7tQN2z3NoSqzpc1Ew7m4nEAhQXDCwZ5aPcS1ya6xhy)          |
| 3o5cfcL9VS31T9N5ZbQgLTHokpxiWbTtjoAMjUp2SNey | [NFT 16](https://solscan.io/token/CYLRkQLuuyACSs1ZSP5uz3iyDiM9BFW3WxrtXhQMVDKH)          |
| 9unenHYtwUowNkWdZmSYTwzGxxdzKVJh7npk6W6uqRF3 | [NFT 17](https://solscan.io/token/BmC5xLibp2pY5gCj4PTBRuYx91SQsT9Y1iRxQpDQoSmm)         |
| 3dTSLCGStegkuoU6dc75DbRdJk4rKV3d5ZCZdSWbTcQv | [NFT 18](https://solscan.io/token/6StYMmHFsSf3FQfGGHJZeGpYCGLY186tVfExnBbPHdMa)          |
| 6ggGtCSpE6moyjDhQQ7MfQ8cw89DcgtYJhaKZaKJ59CQ | [NFT 19](https://solscan.io/token/6AUbboXuuJ1vJYTzohbnCW1DWLDRsmSZp5FRor3LaYct)          |
| 9riZWGcTFTLoBpmRM5xfYXCrHsxoqL4ynqBYtNxskYHV | [NFT 20](https://solscan.io/token/5tMNtot88F7MtGmpxC49Zs1w8d136o4jsetChPsGrS4W)          |
| JCsFjtj6tem9Dv83Ks4HxsL7p8GhdLtokveqW7uWjGyi | [NFT 21](https://solscan.io/token/22qakvysK11FgUaU2J9K1rPmPsbGja9h4mzCMRGmnRAp)          |
| DH9oe9rfZWkRfBVWvib11ihrgCaYP1jGrD9fXcvhun37 | [NFT 22](https://solscan.io/token/9JhaCnntwRD7FAF1NVW12m9974cs9saGsAG7UnwWf83D)          |
| 7jQFJLS3QRGJyshYkLgp4QQH8D5c9qym2LQzkhag38UD | [NFT 23](https://solscan.io/token/3uHuu5FKkJBNUsPF2RkTin3k3jCvidwp2PhnEGNiBoq4)          |
| HdaKENyK8fxod85QipFYZffC82PmsM8XEW4prcZbeQiK | [NFT 24](https://solscan.io/token/Hnr8hJcbqZySR1DMtyX1sQub3CHAKo2R7KWX2yEBqYp9)          |
| EcrHvqa5Vh4NhR3bitRZVrdcUGr1Z3o6bXHz7xgBU2FB | [NFT 25](https://solscan.io/token/ELSDkR6Lo1ze3t795ZZRtW9nAh1RkHgjms5ZwiCjEkuS)          |
| GyETGp22PjuTTiQJQ2P9oAe7oioFjJ7tbTBr1qiXZoa8 | [NFT 26](https://solscan.io/token/QSh7kmCeT1gAKXMuHCwkg7jaywX9X2Cp3V4guUJRQgt)          |
| frae7AtwagcebTnNNFaobGH2haFUGNpFniKELbuBi2z | [NFT 27](https://solscan.io/token/6hTqXDMauaXphncwNGWrzec1HPvfjjQGnXSPvkDEa5kb)          |
| 38rc27bLd73QUDKmiDBQjsmbXpxinx8metaPFsRPSCWi | [NFT 28](https://solscan.io/token/6v6kQpqEZ47Dtugv5kFhyrMdHti56emfyPcaBUdtPnt5)          |
| 4syk2oXfU7kgpAPAxsyBv47FHeNuVz5WGc2x8atGNDd2 | [NFT 29](https://solscan.io/token/GFtes6HLygmpeLyEMuonnPkWTFLdZUq1k1YjNwsWncwq)          |
| HFJEhqTUPKKWvhwVeQS5qjSP373kMUFpNuiqMMyXZ2Gr | [NFT 30](https://solscan.io/token/FR8V41SzwE9WUwSKspLH27wKdyGj4BUFjWNonyyysfmp)          |
| 72hBoHW3TDBHH8vASheaqwVAb8ez3SJAhwtegN5UQvJ9 | [NFT 31](https://solscan.io/token/DjsKCcAj3jVPERnV1VLQJq3s64aCEXT5atNMGw4NPYin)          |
| CxjawXnJxAyb7Zx3xCkSD3nxamdpcfSikvnnC7C8RMHh | [NFT 32](https://solscan.io/token/8JnhHDYoBzuwFdoF5JyMhZpPaskrHKnGtTTt3dQxA6xD)          |
| A1mq3dn2tUBfJB6WjnL4XtVQgGLGAUD3FeiMLuUQoRMu | [NFT 33](https://solscan.io/token/F9mVXQEDcJ6gmLniPKuikBnSXgQzZUH5ThXFSGnQY62U)          |
| 2hNdA3G3hfwUN6z28mgFTAjmkXdTvHsRiTXQP3AZjaij | [NFT 34](https://solscan.io/token/4vV3QvNDJ311FYaveKtgzLFU2xiaeeiuP3YcuNwiApXb)          |
| ji1E9W3P4Yesmwcv6m5rgBs6dGnshaTcfaFoRW6qcjL | [NFT 35](https://solscan.io/token/4tacAiKgqWfofiEb1mMkkwqHMHHtwxocPXNbMd6oM6k2)          |
| HT8DNntQe2ZN1v763zUqPou5wwNGTg6xBPCDg31vhjrv | [NFT 36](https://solscan.io/token/4KW6B4zUHqtK7DgudLA3Fqw1Ai8Cq9pvZKeAgbw8xcC4)          |
| BsdgGRzDmVTM8FBepRXrQixMZgjP6smsSbuDb1Y7VJB6 | [NFT 37](https://solscan.io/token/BZmaJTMv3juo2ZVeru7VgaUoB6ZaCqmfdmPdAysshYfL)          |


---

## Conclusion

Completing this project was both demanding and enlightening. It pushed me to explore new areas of blockchain technology and refine my problem-solving skills. I'm grateful for the experience, as it has prepared me for more complex challenges in the future.

---

## Acknowledgments

I would like to thank my mentors and peers in the fellowship program for their support and guidance throughout this project. Their insights were invaluable.

---

**Thank you for reviewing my project!**

If you have any questions or would like to discuss any aspect of this project further, please feel free to reach out.