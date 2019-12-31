# Blockchain Surveillance

## Guilty by Association
Those with technical knowhow or money to buy it, will be able to track transactions through the blockchain, even if you have escaped the fiat payment panopticon by doing the following:

1. Buy your product. Pay for it with bitcoins and make a note of the bitcoin receipt address. This provides snoopers with a known address that you control and serves as a starting point for their blockchain tracking.
2. Set an alert for when bitcoins are sent from the receipt address they used to pay you. This lets them know that you are moving the bitcoins they sent you.
3. If the bitcoin transaction used to spend coins from your receipt address includes inputs from other bitcoin addresses, they can assume that you also controlled these coins as well. Evaluating the additional inputs may lead to information about other customers and purchases. Now they're going to track them back and see if they can doxx those customers as well.
4. They will keep watching the bitcoin move and see if they can associate your outputs with other known entities. Who are your suppliers or infrastructure providers?

For a real account of blockchain analysis check out ErgoBTC's tale of [Tracking the PlusToken Whale](https://medium.com/@ErgoBTC/tracking-the-plustoken-whale-attempted-bitcoin-laundering-and-its-impact-on-wasabi-wallet-787c0d240192)

## Routing through Lightning
So how do you thwart this? One way is to use Lightning. Since lightning payments use an onion routing system, you can't audit the lightning payments, only opening and closing channel payments. Lightning isn't perfect privacy, but it's similar to TOR in that whatever happens between exit nodes is difficult to track.

## Majestic Mixing
Another way to protect yours and your customers' privacy is to Coinjoin any on-chain payments. Samourai Wallet's [Whirlpool](https://github.com/Samourai-Wallet/Whirlpool) is a great tool for mixing. The Coinjoin transactions will help break the link between your coins' past and future transaction history. This is not a privacy silver bullet, but coinjoin makes the analysis described above extremely difficult if done properly.

For Whirlpool, inputs should be greater than or equal to multiples of whatever denominated pool you choose to participate in. For example if you're in x pool, you need at least x bitcoins to fund that transaction plus miner and mixing fees. Ideally you would coinjoin more than 2x the pool size to reduce your fee paid. If you have 0.8x (let's call this UTXOa), sorry you'll have to complete another transaction in which you combine it with something at least 0.2x (UTXOb) and *then* move that 1x into the Whirlpool mixer. Merging UTXOa and UTXOb is a problem, because blockchain spies will assume that a single entity controlled these coins. This can be damaging to yours and your customer's privacy, because now you've linked a and b, which we are trying to avoid. Using Samourai Wallet's Ricochet transaction feature to send these UTXOs to yourself will put distance between your receipt transactions and mix transactions. Samourai Wallet also has additional transaction tools such as STONEWALL (which are mini-fake coinjoins) that allow users to merge UTXOs in a transaction with better privacy than a normal bitcoin transaction. Neither of these tools are foolproof, but again they make the analysis described above more costly.

## A Tedious Combination
Another possible solution would be to make use of two lightning nodes that are not directly connected to move funds across the lightning network through routing nodes and then combine those funds (different UTXOs at that point) on the other end into a Tx0 address. I'm still working on smoothing out the explanation of this. It's also very tedious because each UTXO has to individually be moved from whatever wallet it's in to a Lightning wallet, then to a lightning channel, then the value moved across the lightning network to a channel on your second node, then that channel closed and only then can you combine those other UTXOs to one Tx0 input. I'm hopeful that we can get some sort of coinjoin included into BTCPay in the future and I'm also hopeful for the possibilities with LoopOut as it gets developed. If you have more suggestions, please contribute to the Github repo.

For more examples of how parties can be identified by their bitcoin behavior, follow [LaurentMT](https://twitter.com/laurentmt) and [ErgoBTC](https://twitter.com/ergobtc) on Twitter.