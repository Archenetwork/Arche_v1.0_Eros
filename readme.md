# Arche_v1.0 Eros Core Contract
## Introduction

Arche Network is a user-defined open platform based on Ethereum, Polygon and BSC. It aims to empower
traders and developers to participate in a customized asset marketplace by providing user-friendly
tools and community support that is open, and assessable to all. Arche Network v1.0 contract is
called Arche_v1.0 Eros, users can create a token swap with customized parameters.

## Functions/Interfaces
Here are 2 Contracts,Main-Contract and Factory-Contract.
### Main Contract

| Function Name | Brief Introduction |
| --- | --- |
|Set_Arche_Address(address addr) | Set Arche token address (DEPLOYMENT ONLY) |
|Set_Trading_Charge_Lib(address lib) |Set Trading Charge lib address (DEPLOYMENT ONLY) |
|Set_Arche_Amount_Per_Deal(uint256 amount) | Set the fee (token amount) of one deal (DEPLOYMENT ONLY) |
|Set_Token_Collecter(address addr) | Set the collector addresss, any fee will be send to the address (DEPLOYMENT ONLY)|
|Set_Factory_Lib(address addr) | Set Address of Factory contract (DEPLOYMENT ONLY) |
|Create(address token_head,address token_tail,address sys_reward_addr,uint256 sys_reward)  | Create an Option Ticket from Factory Contract .Caller shall invoke approval of correct Token contract before this action <ul><li> this reward token of contract address "sys_reward_addr" will be distributed to referers  </li> <li>the total amount of referers' reward is "sys_reward"</li></ul>|
    
### Factory-Contract

| Function Name | Brief Introduction |
| --- | --- |
| Set_DSwap_Main_Address(address addr)   | Set Address of EMain Contract (DEPLOYMENT ONLY) |
| Set_Initializing_Params(uint256 total_amount_head ,uint256 total_amount_tail ,uint256 future_block_offset,string memory slogan)| Option Creator Set parameters of Option .<ul>   </li> <li> "total_amount_head" and "total_amount_tail" means amount of token. creator will swapping from "total_amount_head" head token to "total_amount_tail" tail token.  </li> <li>   "future_block_offset" indicates how many blocks until the dell will close.  </li> <ul>  |
| Claim_For_Head() |Option deal creator address claim for the option (HEAD side)|
| Deposit_For_Tail(uint256 amount,address referer)| Any address pay ERC20 of the option (TAIL side) <ul><li>"amount" means that the caller spends amount tail token.</li><li>the address "referer" referred this order to caller </li></ul>|
| Claim_For_Delivery() | When the future is closed ,invoke this function to claim token(s) |
| Withdraw_Head() | If there is no rival, send tokens back and obliterate this deal |
