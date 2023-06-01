# ShadowPounds
Shadow Currencies - tokens that shadow a real currency

I am introducing to the world "Shadow Pounds" and its accompanying "Shadow Currencies": "Shadow Greens" (USD) and "Shadow EURO".

The way they work is simple: a user converts an ETH token into one of these tokens using the ETH exchange rate to the denoted fiat currency. This means if an englishman with GBP buys ETH and then buys Shadow Pounds, he is ending up with an amount of Shadow Pounds that corresponds to his intial GBP savings. Of course, being an ERC-20 token, it will be expressed as a much larger or smaller number (i.e. instead of 1.00 gbp buying 0.00067 ETH buying 1.00 SGBP (Shadow Pounds), the Shadow Pounds will have the decimal point in a different place). Essentially though, it will "shadow" the pound, meaning that any increase in pounds traded will proportionally increase the shadow pounds. This "shadow" token is porportional to the original fiat currency.

So how to make money with this? It's not strictly for making money, as it's a stable coin, but you could wait for ETH to drop against SGBP and trade back to ETH from SGBP. You'll have to pay a 1% fee to trade back but you'll need less SGBP than you have to get your original ETH balance. What to do with the rest of the SGBP? Sell it to someone who neeeds it - and they will need it.

You see, if ETH goes up against SGBP (which it will most of the time), to trade back to ETH will require a larger amount of SGBP. One way to obtain that SGBP is to enlarge the position (a function in the ERC-20 token contract) but another way would be to buy it from someone who has excess SGBP which they can't turn into ETH. Therefore there will be a ready market for these shadow currencies.

So a quick walkthrough of the trade-relevant functions in the contract and their use in the Remix IDE program:

1) To convert to a shadow currency, simply use the "openposition" function to open a position in the shadow currency. In Remix, denote the amount to buy in the "value" box of the "deploy and run transactions" tab of the program.
2) To convert back, or close the position, one must note the price change since opening the position. These contracts use chainlink to calculate the prices for the fiat currencies and the chainlink prices for ETH and other tokens can be found here: https://data.chain.link/ Use the Ethereum mainnet prices. As there are no prices for ETH/GBP, I have simply divided ETH/USD by GBP/USD. The same for the EURO. Once you have found the prices for ETH in the desired currency, you can determine if you require more shadow currency to close the position (if the ETH price has gone up) or if you can close the position with excess shadow currencies - which you can later sell.
3) If you require more shadow currency to close the position, there is an "enlargeposition" function. Simply calculate how much you require to enlarge it by in order to successfully close the position. (Or you can simply buy shadow currencies from someone else).
4) Closing the position is simply the "closeposition" function. Remember that there are 18 decimals in the tokens in these contracts, so any value you enter must be multiplied by 10^18 and with no decimal points. This number goes in the "uint256 value" labelled box. Also remember to enter the fee in the "value" box of the "deploy and run transaction" tab. This fee is 1% of the initial opening position. Don't forget, if you can close the position with excess shadow currencies, do so. Don't just enter in the amount you received in the initial position opening. Do the math! Work out how much you can profit.

Happy trading!

Here are the addresses for the contracts:

Shadow Greens (USD) - 0x64F7a82Bb13a773F641cd77c8B92A39E8a94D7eD

PS: I am stuck in Rishi Sunak's garden shed like in Shawn of the Dead, so I turned to coding to help pass the time. https://www.youtube.com/watch?v=ihKYI2fpTA8
