# Single Asset LP
Single asset deposits can allow lending protocols to present a simple UX to usrers by simply having an option with their usual "Lend your USDC" to have an sAMM enabled boosted deposit with like "Lend your USDC + sAMM Boosted" to allow depositors to choose between single asset lending directly with known APY / interest rate or assume IL risk but also earn swap fees from the sAMM as well as the interest fees.

## Flow
1. User deposits single asset to the sAMM.
2. sAMM swaps asset x to asset y until the target sAMM asset balance for x/y target using either the sAMM itself or other AMMS. The sAMM then deposits the 2 assets as usual to the lending protocol using the assets as needed during swaps and earning fees.
3. When the user wishes to withdraw, deposits are withdrawn from the lending protocol as usual, but the y asset swapped back to x asset before returning to the user. This exposes the user to both assets interest rates according to the AMMs balances as well as IL, but gives them AMM swap fees. This is best for like kind assets such as USDC and FEI or atleast closely tracking assets like ETH and BTC.
