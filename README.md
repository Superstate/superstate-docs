# Superstate Basics

## What are Superstate AMMs?
Superstate Automated Market Makers are AMMs that earn yield on assets by keeping the balances in the APY optimal protocols until they are needed to execute swaps. We do this through snmulated balances to keep compatibility and composabtlaty with front ends and contract interfaces.

## Why Superstate? What makes it better than other AMMs? Isn't this just another Uniswap clone?
Superstate might look like another swap fork, but under the hood there's a simple but powerful difference. We make LP assets not just there for liquidity but we make them productive! By using protocols like Aave, Yearn and more we allow LP deposits to earn yield as well as swap fees. The balancer makes sure that when needed assets can be used for swaps and that theres a comfortable cushion for most swaps to be gas efficient for L1 or have full deposit and achieve superstate for L2s (cause gas fees are much lower), but we also allow automatic rebalancing and full access to the deposit assets as needed to not impact user experience during a trade. As an LP you get the best possible return getting yield from swap fees AND lending at the same time, with interest being paid to the LP token the same as the swap fees.

As a user you get access to better liquidity because now deposits from LPs can access both revenue streams and dont need to choose. So you get better rates and lower slippage.

Basic flow for LP
1. The LP provides both assets as they would any other AMM.
2. The AMM deposits the balance into the APY protocol, and increases the virtual balances for the contract held by the APY protocol as deposits, allowing those balances to be used rather than jnternal balances for pricing.
3. The assets earn yjeld through loans, vaults, whatever mechanism s being used passively, creating depth for the APY protocol using the AMM s assets.
4. When a swap happens the trader pays a fee, which also gets deposited for further interest, earning the LP both swap fees and interest from the APY protocol. s
5. The LP wishes to withdraw, net balances are checked and the LP gets their assets + AMM fees + APY interest.

User flow
1. The user checks the rate for asset x to asset y using the standard AMM mechanism, but uses deposits to the APY protocol + internal assets (usually 0) to get the rate, not affected by deposits not being in the contract before the tx.
2. The contract swaps the token x for y at the set rate and withdraws the needed y amount, sending to the user.
3. The x token gets deposited for further APY.

We call this mechanism superstates as the assets are effectively in 2 places at once and earn both revenue sources as if they were only in that protocol through a neat trick using virtual balances.

