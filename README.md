# ShadowGreens
Shadow Greens - a token that shadows the US Dollar.

I am introducing to the world "Shadow Greens".

The way it works is simple: a user converts an ETH token into one of these tokens using the ETH exchange rate to the denoted fiat currency. This means if an American with USD buys ETH and then buys Shadow Greens, he is ending up with an amount of Shadow Greens that corresponds to his intial USD savings. Of course, being an ERC-20 token, it will be expressed as a much larger or smaller number (i.e. instead of 1.00 USD buying 0.00067 ETH buying 1.00 SGRN (Shadow Greens), the Shadow Greens will have the decimal point in a different place). Essentially though, it will "shadow" the USD, meaning that any increase in USD traded will proportionally increase the shadow greens. This "shadow" token is porportional to the original fiat currency.

So how to make money with this? It's not strictly for making money, as it's a stable coin, but you could wait for ETH to drop against SGRN and trade back to ETH from SGRN. You'll have to pay a 1% fee to trade back but you'll need less SGRN than you have to get your original ETH balance. What to do with the rest of the SGRN? Sell it to someone who neeeds it - and they will need it.

You see, if ETH goes up against SGRN (which it will most of the time), to trade back to ETH will require a larger amount of SGRN. One way to obtain that SGRN is to enlarge the position (a function in the ERC-20 token contract) but another way would be to buy it from someone who has excess SGRN which they can't turn into ETH. Therefore there will be a ready market for this shadow currency.

The best thing about this shadow currency is that it is a neutral asset, meaning if you open a position in Shadow Greens from ETH with funds sourced from USD, you do not stand to gain or lose with respect to the starting currency (USD) but you CAN gain or lose with respect to ETH. Whatever you lose with respect to ETH won't create losses with respect to USD (except for the 1% fee). So you are betting on the weakness of ETH without risking any USD. In the long term, it won't work as USD is inflationary and ETH is deflationary and you will have to keep enlarging your position but you won't lose anything with respect to USD - but you stand to gain in the short term if ETH dips. So you're essentially betting for short term gains with almost no risk (the risk is you'll need to keep enlarging your position and you still need to pay the 1% fee).

So a quick walkthrough of the trade-relevant functions in the contract and their use in the Remix IDE program:

1) To convert to the shadow currency, simply use the "openposition" function to open a position in the shadow currency. In Remix, denote the amount to buy in the "value" box of the "deploy and run transactions" tab of the program.
2) To convert back, or close the position, one must note the price change since opening the position. This contract uses chainlink to calculate the prices for the fiat currencies and the chainlink prices for ETH and other tokens can be found here: https://data.chain.link/ Use the Ethereum mainnet prices. Once you have found the prices for ETH in USD, you can determine if you require more shadow currency to close the position (if the ETH price has gone up) or if you can close the position with excess shadow currencies - which you can later sell.
3) If you require more shadow currency to close the position, there is an "enlargeposition" function. Simply calculate how much you require to enlarge it by in order to successfully close the position. (Or you can simply buy shadow currencies from someone else).
4) Closing the position is simply the "closeposition" function. Remember that there are 18 decimals in the tokens in these contracts, so any value you enter must be multiplied by 10^18 and with no decimal points. This number goes in the "uint256 value" labelled box. Also remember to enter the fee in the "value" box of the "deploy and run transaction" tab. This fee is 1% of the initial opening position. Don't forget, if you can close the position with excess shadow currencies, do so. Don't just enter in the amount you received in the initial position opening. Do the math! Work out how much you can profit.

Happy trading!

Here is the address for the contract:

Shadow Greens (USD) - 0x64F7a82Bb13a773F641cd77c8B92A39E8a94D7eD

PS: I am stuck in Rishi Sunak's garden shed like in Shawn of the Dead, so I turned to coding to help pass the time. https://www.youtube.com/watch?v=ihKYI2fpTA8
