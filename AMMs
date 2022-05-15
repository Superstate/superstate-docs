# Superstate AMMs on L2
By using L2s we can have low gas fees and have all assets be used across both the AMM and lending pools at the **same time**. We do this by having the AMM virtualise balances that are deposited to preserve the fundamental AMM mechanism that all AMMs share for prices, without actually having the assets in the AMM. When a transaction happens the amount outs withdrawn and the inputs deposited to further the yield. This allows for the assets to operationally be in both pools at the same timeandand with both APY sources being fully used, and users able to access deeper markets as liquidity can be shared as one.
The balances are virtualise d by simply changing the source for the balances lookups to the deposit mappings rather than internal balances. This trick allows the front end to show the reserves as if they were in the protocol rather than deposit eed at any time without them actually needing to be in the AMM, allowing for depth, slippage, rates, all interfaces and front ends to operate as if was any AMM, but with LP s earning yjeld. there ed ly

### Basic flow for LP
1. The LP provides both assets as they would any other AMM.
2. The AMM deposits the balance into the APY protocol, and increases the virtual balances for the contract held by the APY protocol as deposits, allowing those balances to be used rather than jnternal balances for pricing.
3. The assets earn yjeld through loans, vaults, whatever mechanism s being used passively, creating depth for the APY protocol using the AMM s assets.
4. When a swap happens the trader pays a fee, which also gets deposited for further interest, earning the LP both swap fees and interest from the APY protocol. s
5. The LP wishes to withdraw, net balances are checked and the LP gets their assets + AMM fees + APY interest.

### User flow
1. The user checks the rate for asset x to asset y using the standard AMM mechanism, but uses deposits to the APY protocol + internal assets (usually 0) to get the rate, not affected by deposits not being in the contract before the tx.
2. The contract swaps the token x for y at the set rate and withdraws the needed y amount, sending to the user.
3. The x token gets deposited for further APY.

### Assumptions
We make 1 fundamental assumption.
1. All assets are available for withdraw at any given time. This assumption relates to LPs being able to withdraw and as a requirement for what protocols we use, as we will not use any with a timelock.
1. A. We assume that there are enough assets for almost all swaps based on availability by the APY protocol (lending pools may have full capacity and as such we would not be able to withdraw during a tx). This can be safely assumed as almost always lending protocols have some spare capacity, using relative and dynamic fee rates to guarantee that. 

