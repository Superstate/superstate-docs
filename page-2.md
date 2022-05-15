# Layer 1 Page 2

Layer 1 mainnet has higher fees so for this we adopt partial superstate.
### Basic flow for LP
1. The LP provides both assets as they would any other AMM.
2. The AMM deposits the balance * .2 into the APY protocol, and increases the virtual balances for the contract held by the APY protocol as deposits, allowing those balances to be used rather than internal balances for pricing. Net balances are deposit + internal
3. The assets earn yield through loans, vaults, whatever mechanisms being used passively, creating depth for the APY protocol using mostthe AMMs assets.
4. When a swap happens the trader pays a fee, which also gets deposited for further interest, earning the LP both swap fees and interest from the APY protocol. s
5. The LP wishes to withdraw, net balances are checked and the LP gets their assets + AMM fees + APY interest.

### User flow
1. The user checks the rate for asset x to asset y using the standard AMM mechanism, but uses deposits to the APY protocol + internal assets (about .2x as the threshold) to get the rate, not affected by deposits not being in the contract before the tx.
2. The contract swaps the token x for y at the set rate, during usual operation the threshold allows for a dedicated liquid threshold to be kept so that swaps do NOT withdraw from APY protocols, during high volatility or for large trades the contract threshold may be reached and withdraws the needed y amount, sending to the user. The contract will target a threshold between .2x and .07x assets in the internal balances so that swaps are kept internal and cheap with arb being used to keep prices and so balances around the target.


