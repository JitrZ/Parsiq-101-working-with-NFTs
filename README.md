# Parsiq-101-working-with-NFTs

## Introduction

Parsiq is a blockchain monitoring and workflow automation that has easy setup and perfect tools. First, I create a trigger to monitor CryptoassaultunitNFTs, an innovative MMO strategy blockchain game that is a play-to-earn game (ASLT token to earn), and its recent development and new Cryptocommnaders NFT has attracted many users. Secondly, I use Parsiq tools to analyze UniswapV3 positions by monitoring V3positionsNFT and use this analysis for a good decision on the Uniswap app either as a liquidity provider or trader.

Thanks to [the walkthrough](https://dspyt.com/generating-fast-and-easy-parsiq-triggers-for-cryptopunks) created by @Pfed-prog and the Parsiq docs and video tutorials, it's easy to learn and create a simple trigger and get results from that. I get the ABI from [Cryptoassault contract](https://etherscan.io/address/0x31af195db332bc9203d758c74df5a5c5e597cdb7) and [UniswapV3 Positions NFT contract](https://etherscan.io/address/0xc36442b4a4522e871399cd717abdd847ab11fe88). Then, in Parsiq I create new userstreams with these ABIs and choose events and functions that I want to use in triggers for my purposes. Also, I use google sheets for transports. Finally, I created triggers by events and functions for each purpose to analyze further the results.

### CryptoAssault NFT

My purpose of using Parsiq for CryptoAssault NFT was to track Minting and Transfering events. For minting, there are two ways; Using the mintAndSetData functions in [trigger](https://portal.parsiq.net/monitoring/projects/56acd610-7b1e-4d8f-9996-3c7fd485b727/triggers/5618ed82-d32d-426a-bf8d-2e5e354950d3), Using the Transfer event in [trigger](https://portal.parsiq.net/monitoring/projects/56acd610-7b1e-4d8f-9996-3c7fd485b727/triggers/a7350c84-490f-4d62-9e58-495831c3a706) with the condition that "_from"_ address is "0x0".

![image](https://user-images.githubusercontent.com/41538734/140824417-ca57cb89-a107-4472-a585-8629d8f234d8.png)

![image](https://user-images.githubusercontent.com/41538734/140824609-be00ba58-8389-4b03-bc9c-30092fa175a5.png)

To [alert](https://portal.parsiq.net/monitoring/projects/56acd610-7b1e-4d8f-9996-3c7fd485b727/triggers/f31ab39a-2fbd-4735-8e3d-f5b8cb9160a7) about the transfers of CryptoAssault NFT, I use the Transfer event, this time with the condition that "_from"_ addres is not "0x0".

![image](https://user-images.githubusercontent.com/41538734/140825230-3baa63dd-ac27-41a2-bcf3-44a1ed8d3fa3.png)

For more analysis, I want to use triggers of *totalSupply*, *balanceOf* and *getData* functions. With CryptoAssaultUnits and upcoming CryptoCommanders NFT, I can merge this two NFT analysis and the ERC20 token ASLT to provide a clear view on the economy of this game to help both the game developers and players.

### UniswapV3 Positions NFT

UniswapV3 has provided pool liquidity providers the ability to set their liquidity and the minimum and maximum ticker to manage their position, so they can have more access to manage their LP tokens and the income and loss. Each position in V3 is an NFT and has its token_id. My idea is to monitor this NFT minting (to know about the positions created in the pool) and extract the *params* data. Informations such as the pair liquidity provided and minimum and maximum ticker and the amounts could help both liquidity providers and traders to do a better desicion. Also, the increase liquidity and decrease liquidity events are two other important things to alert users which pools liquiidty have changed.
So, I decide to [trigger](https://portal.parsiq.net/monitoring/projects/56acd610-7b1e-4d8f-9996-3c7fd485b727/triggers/50502eca-ff8b-450d-90c7-3f2d2d6d4a79) mint function to track pools and extract data from *params* struct. But couldn't find a way yet to access this struct variables. This struct has many important infomration such as the pairs, the tickers and the amounts that could be used for more analysis. (Parsiq Stream explorer is another great tool but it gets to problem in this step and seems have problem with @params struct variable and gets to blank page after interacting with the Stream explorer)

![image](https://user-images.githubusercontent.com/41538734/140827314-19477f15-df69-441f-9bad-f3c3dbf61998.png)

In addition I [trigger](https://portal.parsiq.net/monitoring/projects/56acd610-7b1e-4d8f-9996-3c7fd485b727/triggers/80933373-5f99-40d8-ac8a-3015a10cac7e) change liquidity events to know about the change amounts in positions (each token_id):

![image](https://user-images.githubusercontent.com/41538734/140827674-cd591ae6-36b1-4487-a25f-73a69bd5ed0d.png)


## Conclusion

I've worked with different blockchain querying and monitoring tools these months. PARSIQ is a great new platform with innovative ideas that could help blockchain developers and researchers to get into the blockchain world more easily and extract what they want. PARSIQL language and the other tools inside the portal are great, and PARSIQ is developing perfectly to fit different use cases. My recommendation would be more access to free users, so more people will join. Thanks to the PARSIQ platform, I will be able to continue working on my two ideas; First, tracking the CryptoAssault game economy. Second, monitoring Uniswap V3 positions to make better decisions either as a liquidity provider or trader. At the end, here's my project id on PARSIQ: 56acd610-7b1e-4d8f-9996-3c7fd485b727 if anyone wants to contribute.
