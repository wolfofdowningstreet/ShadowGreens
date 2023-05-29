# ShadowPounds
Shadow Currencies - tokens that shadow a real currency

I am introducing to the world "Shadow Pounds" and its accompanying "Shadow Currencies": "Shadow Greens" (USD), "Shadow OZ" (AUD), "Shadow Yen", "Shadow CAD", "Shadow Francs" (CHF), "Shadow Rupee" (INR) and "Shadow EURO".

The way they work is simple: a user converts a MATIC token into one of these tokens using the MATIC exchange rate to the denoted fiat currency. This means if an englishman with GBP buys MATIC and then buys Shadow Pounds, he is ending up with an amount of Shadow Pounds that corresponds to his intial GBP savings. Of course, being an ERC-20 token, it will be expressed as a much larger or smaller number (i.e. instead of 1.00 gbp buying 1.32 MATIC buying 1.00 SGBP (Shadow Pounds), the Shadow Pounds will have the decimal point in a different place). Essentially though, it will "shadow" the pound, meaning that any increase in pounds traded will proportionally increase the shadow pounds. This "shadow" token is porportional to the original fiat currency.

So how to make money with this? It's not strictly for making money, as it's a stable coin, but you could wait for the MATIC to drop against SGBP and trade back to MATIC from SGBP. You'll have to pay a 1% fee to trade back but you'll need less SGBP than you have to get your original MATIC balance. What to do with the rest of the SGBP? Sell it to someone who neeeds it - and they will need it.

You see, if MATIC goes up against SGBP (which it will most of the time), to trade back to MATIC will require a larger amount of SGBP. One way to obtain that SGBP is to enlarge the position (a function in the ERC-20 token contract) but another way would be to buy it from someone who has excess SGBP which they can't turn into MATIC. Therefore there will be a ready market for these shadow currencies.

So a quick walkthrough of the trade-relevant functions in the contract and their use in the Remix IDE program:

1) To convert to a shadow currency, simply use the "openposition" function to open a position in the shadow currency. In Remix, denote the amount to buy in the "value" box of the "deploy and run transactions" tab of the program.
2) To convert back, or close the position, one must note the price change since opening the position. These contracts use chainlink to calculate the prices for the fiat currencies and the chainlink prices for MATIC and other tokens can be found here: https://data.chain.link/ Use the polygon mainnet prices. As there are no prices for MATIC/GBP, I have simply divided MATIC/USD by GBP/USD. The same for the other fiat currencies. Once you have found the prices for MATIC in the desired currency, you can determine if you require more shadow currency to close the position (if the MATIC price has gone up) or if you can close the position with excess shadow currencies - which you can later sell.
3) If you require more shadow currency to close the position, there is an "enlargeposition" function. Simply calculate how much you require to enlarge it by in order to successfully close the position. (Or you can simply buy shadow currencies from someone else).
4) Closing the position is simply the "closeposition" function. Remember that there are 18 decimals in the tokens in these contracts, so any value you enter must be multiplied by 10^18 and with no decimal points. This number goes in the "uint256 value" labelled box. Also remember to enter the fee in the "value" box of the "deploy and run transaction" tab. This fee is 1% of the initial opening position and is denoted in MATIC. Don't forget, if you can close the position with excess shadow currencies, do so. Don't just enter in the amount you received in the initial position opening. Do the math! Work out how much you can profit.

Happy trading!

PS: I am stuck in Rishi Sunak's garden shed like in Shawn of the Dead, so I turned to coding to help pass the time. https://www.youtube.com/watch?v=ihKYI2fpTA8
