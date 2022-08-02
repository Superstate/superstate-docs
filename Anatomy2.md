# V1 Flow
1. Deposit assets to Superstate AMM

2. AMM deposits assets to 4626 vaults for asset 0 and asset 1, holds 4626 token balances which then are used to virtualise the underlying balances for front ends / interfaces to look like underlying are in the AMM while deposited, mint LP token to minter.

2. A. Should the target not be 4626 compatible deposit to wrapper/adapter which deposits to target passive protocol.

3. Assets earn passive APY while not needed.

4. During a swap, withdraw purchased token from 4626/wrapper and send to buyer, deposit payment token to 4626 to earn interest.

5. LP withdraws LP by burning LP tokens, gets relative share from 4626 deposits including swap fees, interest and collateral.

# V2. USDc sample
1. Assets (2 USDc and 2 USDt, 2 USDx) are deposited to Superstate vault. Mint LP tokens to minter

2. Assets are then deposited by vault to target deposit protocol(s) and strat earning passive interest, vault refers own balance as the underlying value of deposits.

3. Superstate v2 AMM for USDc / USDt requests funds from vault for swap, using the vaults balances as own liquidity. Must be whitelisted. Vault sends .997 USDc out token to AMM2, which swaps for 1 USDt in and earns swap fee .003 USDc, AMM sends 1 USDt and fee to vault to be redeposited.

Later another swap happens for USDt to USDc, USDt sent, USDc deposited. .003 fee earned to USDt.

Vault earns fees from active use of assets during swap tx execution for AMM 2. AMM2 never has any LP itself and cannot mint or hold own assets, acts as a child module for vault like a child program for the parent program. Modules can be AMMs/lending markets/index swaps/vote bribes where they are designed as child modules that plug into the Superstate vault to earn fees,but sharing the liquidity across all modules simultaneously

4. AMM1 for USDx USDc requests 1 USDc for an 1 USDx swap, .997 USDc withdrawn from deposit, sent, and 1 USDx deposited to an USDx lending market to earn interest and get fees. 

5. USDc USDx AMM2 has a 1 USDc swap to buy .997 USDx. USDx gets withdrawn, sent, USDc paid back, deposited. Small .003 swap fee earned for the 1 USDc.

6. Superstate Lending module requests .5 USDc for a loan from vault with ETH collateral. .5 USDc gets withdrawn and borrow happens for 4w. Earns .005 USDc after repayment. Also deposits ETH for APY at some passvedepost protocol. Vault earns .005 USDc and .00001 ETH.

6. A. A flashloan gets executed by the flashloan module, vault sends flashloan module all USDc, transaction executed, USDc returned with .00005 fee. USDc redeposited. 

7. User withdraws vault LP and has 1.006 + .005 + 0.00005 USDc , 1.003 USDt and 1 USDx, as well as 0.00001 ETH from collateral interest on lendng market. And has earned 2 swap fees from 2 different AMMs, 1 lending market and 1 flash loan module on the same 2 USDc. 
+ As well as .01 for USDc USDt and USDx from passive APY.
