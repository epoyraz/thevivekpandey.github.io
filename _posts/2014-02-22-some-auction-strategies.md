---
layout: default
---
#Some auction strategies
In online ad industry, ad inventory is increasingly sold through Real Time Bidding 
(RTB). In this article, we describe three of the most prominent auction strategies 
used in RTB. All these auctions are sealed bid auctions. (i.e. bidders do not know
about values bid by each other)

##Second price auction
This is an auction method where there is one object to be sold and multiple buyers.
Each buyer bids a value. The highest bidder is awarded the object and he pays the
price equal to the second highest bid value. For instance, if a pen is being auctioned
and P1, P2, P3 bid 70, 50, 40 respectively then P1 wins the auction and
pays 50.

####Truth telling is dominant strategy in second price auction####

What it means is that each participant has an incentive to bid the true value that
he attaches to the object.

Let's see this using an example. Let's say an auction for a pen is taking place.
I value that pen at 50. Then, it is best for me to bid 50. Why?

+ Suppose, I become aggressive and bid 60 instead of 50. Then

  + If highest bid other than mine was more than 60, then I would lose the bid.
    But I would have lost the bid even if I bid 50. So, truth telling is no worse
    than bidding 60.
  + If higest bid other than mine was between 50 and 60, I would end up winning the
    bid and paying more than 50. Since intrinsic value of the pen to is only 50,
    this is a unprofitable proposition for me. In this case, truth telling would
    have avoided this loss and was thus a better strategy.
  + If highest bid other than mine was less than 50, I would win the bid whether
    I bid 50 or 60, and pay same price irrespective of my bid. Hence, truth telling
    is no worse than bidding 60.
+ Similarly, suppose I bid conservative and bid 40 instead of 50. Then

  + If highest bid other than mine is more than 50. I would lose the bid irrespctive
    of bidding 50 or 40. So, truth telling is no worse than bidding lower.
  + If highest bid other than mine is between 40 and 50, say 44 then bidding 40 makes 
    me lose the bid, where has bidding 50 would have led me to win the bid, pay 44
    and make a profit of 6.
  + If higest bid other than mine is less than 40, then I would win the bid regardless
    of bidding 40 or 50.

As can be seen from above, truth telling is never worse off than bidding higher or
lower and sometimes it is better than alternative strategies. Hence, truth telling
is a dominant strategy in second price auction.

####Why auction systems where truth telling is dominant strategy are good####
In case participants are not incentivized to bid their true values, their bids would
be dependent on their guess about other participants' bids. This would lead to 
differing bid values by participants even when inventory quality remains the same.
Thus, revenues of seller would be variable, and that is not desirable by the sellers.

##Generalized second price (GSP) auction and Vickrey Clarke Groves (VCG) auction

They are auction strategies where

+ multiple items are for sale
+ some items are more desirable than others, and order of desirability is same for all participants. 
+ a participant can bid only one bid value
+ a participant can win at the most one item

There are various ways to understand GSP and VCG. In this article, let's consider the 
setting that is suitable for understanding auction in ad space.

Example below is inspired from [this](http://en.wikipedia.org/wiki/Generalized_second-price_auction) wikipedia article.
Let's say there are two ad slots with CTRs of 0.9 and 0.4 respectively (irrespective
of the ad that is shown here). Let's say there are three bidders A, B and C who value
the clicks at 7, 6 and 1 units respectively. They need to pay the seller only if an
ad gets clicked.

Let's say the participants bid values 7, 6 and 1 respectively.

__GSP__

Here is how GSP conducts the auction. Highest bidder, A, wins first slot and pays
the second highest bid (6). Second highest bidder, B, wins the second slot and
pays the next highest bid (1). 

Net value realized by A is (7 - 6) * 0.9 = 0.9

Net value realized by B is (6 - 1) * 0.4 = 2

Net revenue of seller is 6 * 0.9 + 1 * 0.4 = 5.8

GSP has a shortcoming that revealing their true valuations in bids is not always
optimal for the participants. For instance, in above example A can bid 2, 
which leads B to win first slot at 2 units and A to win second slot at 1 unit.

In this case,
Net value realized by B is (6 - 2) * 0.9 = 3.6

Net value realized by A is (7 - 1) * 0.4 = 2.4

Thus, we see that A can realize more value by bidding lower than his true
value.

__VCG__

Here is how VCG conducts the auction. As in GSP, highest bidder, A wins the 
first slot and second highest bidder B wins the second slot.

To calculate the bid value of A, we find how much penalty does A cause to
other participants by being present in the system, and winning the first
slot. If A were not present in the system, B and C would win first and
second slots and derive a total value of 6 * 0.9 + 1 * 0.4 = 5.8. Once
A gets first slot, B derives a value 6 * 0.4 = 2.4 and C derives a value 0.
So, A should pay 5.8 - 2.4 = 3.4.

Similarly, B should pay 1 * 0.4 = 0.4, since this is the value by which C
is harmed by his presence (A is not harmed by B's presence).

In this case, total revenue realized by seller = 3.4 + 0.4 = 3.8

##A few notes##
* Second price auction is a specific case of generalized second price auction where
  there is only one item for sale.

* While truth telling is dominant strategy in second price auction, it is not so
  in generalized second price auction.

* Truth telling is dominant strategy in VCG auction. I have not read the proof for that.

* Revenue for seller is usually higher in GSP, compared to VCG. This is is the case
  for example in above example. I do not know what are the precise conditions in which
  this holds true.

##Where are various auction mechanisms used##
* Second price auction is used by exchanges like doubleclick in auction of display
  inventory. Eg, see [Here](http://static.googleusercontent.com/media/www.google.com/en//doubleclick/pdfs/Google-White-Paper-The-Arrival-of-Real-Time-Bidding-July-2011.pdf)

* Generalized second price auction is used by google to sell search ads. Explained 
  [here](http://www.quora.com/Why-does-Google-use-the-Generalized-Second-Price-auction-to-sell-search-ads-instead-of-Vickrey-Clark-Groves)

* VCG auction is used by facebook to auction to sell their RHS inventory. Explained
  [here](http://www.quora.com/Does-Facebooks-Ad-platform-use-a-Generalized-Second-Price-auction)
