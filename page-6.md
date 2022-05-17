# Smart Router for Fragmentation And Allowing Multiple AMMs Without Affecting Liquidity
We also plan to use a smart router for homoasset AMMs whereby LP s can deposit to the AMM which deposits to their desired lending/APY protocol while still earning fees as if they were all a single reserve.

We do this through having trades router along a smart router, extracting the best rates across all available liquidity for an AMM and the splitting the rest along LPs weighted by liquidity.

Assume the following
        Price.    USDc DAI balances
AMM1     .95       50k 49k 
AMM2       1        5m 5m

## Router execution
Sort best rate to worst, then see how much can be swapped until best 1 matches best 2. Then split. Repeat until all available LPs are matched and then split.

So for a 100k USDc swap
1. sort both
AMM1 has a better price by .02x but only 50k LP. So to make AMM 1 and 2 the same need 490 USDc to swap to AMM1.
So allocate 490 to the swap.
490 gets sent, 510 out cause the premium .02x
Now there's 49490 and 49490 so price 1, parity with AMM2.

2. Now weight the 2 pools.
AMM2 has 100x the liquidity so gets .99x the swap which sends (100k-490)*.99 to AMM 1 which now has 5,098,510 and 4,901,490
thats 0.96 price and say AMM takes a .02x fee thats a +0.0004x APY

3. Then .01x from the swap so 995.1 gets swapped with AMM 1, so now thats
50485 USDc 48495 DAI
0.96 price
+0.0004 APY on swap fees

As you can see they get the same fees, that they are perfectly balanced, and that acts as 1.
