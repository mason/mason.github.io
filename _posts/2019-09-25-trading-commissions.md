---
layout: post
title:  "Commissions in trading matter and you should pay attention to them"
date:   2019-09-25 15:03:00 -0500
categories: [trading, futures]
permalink: commissions-in-trading-matter
---

**Disclaimer**
I am not responsible for any losses incurred as a result of reading or implementing ideas or strategies posted on this blog. You(the reader/visitor) are ultimately responsible for your own actions and decisions.
--- 

A few months ago I was going over some futures statements from td ameritrade and noticed something peculiar. I had made 4 trades for the day and was up $150. In those 4 trades, I was trading 3 contracts of /ES futures per trade.

My trades were as follows:

|Type   |Buy     |Sell    | Tick's collected |
|-------|--------|--------|-------------------
|Long   |2930    |2927.5  | -10              |
|Long   |2930    |2929.5  | -2               |
|Short  |2920.5  |2922.5  | 8                |
|Short  |2911.25 |2913.25 | 8                |

As you can see. I ended the day with 4 ticks. With 3 contracts that is 12 ticks. Each tick in the /ES contract is worth $12.50 so I made $150. However, upon checking the transaction statement from TD ameritrade, it stated I had only made $67.20. That's strange! Where did the money go? If you had guessed commissions then you would be right, but the answer isn't so clear.

The breakdown from TD commission structure for /ES futures is as follows. 

|Type         |Cost   |
|-------------|-------|
|Commission   | 2.25  |
|Exchange Fee | 1.18  |
|NFA fee      | 0.02  |


In total, one would pay $3.45 in commission+fees for just 1 contract per one way trip. In other words, to open and close a position for 1 contract it would cost $6.9. In my case, I had 3 contracts per trade so I ended up paying $82.80(4 round trip trades * 3 contracts each trade * $6.9 per round trip). Finally, my gains minus commission+fees was $67.20. Essentially I paid over 50% of my gains in commissions in fees. **Pretty horrible**.

With that said, I did end the day barely green with +4 ticks. This is equivalent to the /ES gaining $1. If I had ended the day with say +8 ticks, the fees would stay the same but I would have made $217.20. Earlier, I mentioned that the answer to where the money went wasn't clear. What I meant by that is that TD's website doesn't clearly expose the costs of trade. If you visit their [fees page](https://www.tdameritrade.com/pricing.page), they mention that futures commission is $2.25 per contract but they don't disclose what the exchange or NFA fee would be. In their defense, listing the exchange fee would be cumbersome as they can be different per futures contract type. They should still have a link that clearly states the fees per contract type somewhere on that page.


With that said, I went shopping around for what other brokerages were offering in terms of fees for futures. [Tradovate](https://www.tradovate.com/), for example, offer a few tiers of pricing. For the sake of simplicity I will just look at their free tier. According to their website, their fee structure for the free plan is as follows:

|Type         |Cost   |
|-------------|-------|
|Commission   | 0.79  |
|Exchange Fee | 1.18  |
|NFA fee      | 0.02  |
|Clearing Fee | 0.09  |

In total, one /ES contract per one way trip would be $2.08. This is around 40% less in commission and fees. If I did the same trade as the example above, I would be paying $49.92 ($4.16 commission and fees * 4 round trip trades * 3 contracts each).

As you can see, commission+fees can have a large impact on bottom line P&L. With that said, TD has one of the best platforms out there. The tools available may be worth the price if your strategy depends on them.

