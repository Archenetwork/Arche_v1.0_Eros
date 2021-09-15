

# Main Contract
## Methods
- Create:\
This Method create an Option Ticket from Factory Contract,thus users can swap tokens with contract "token head" and "token tail". Caller shall invoke approval of correct Token contract before this action. This method return a sub contract address created by this contract .The reward token of contract address "sys_reward_addr" will be distributed to referers. The total amount of referers' reward is "sys_reward".\
\
Interface:

        Create(address token_head,address token_tail,address sys_reward_addr,uint256 sys_reward) returns(address)  


## Variables

- m_Arche_Amount_Per_Deal: Main Contract will Take ArcheToken with amount of "m_Arche_Amount_Per_Deal" for fee.

- m_Address_of_Arche_Token: Contract address of ArcheToken.


# SubContract

## Methods

- Set_Initializing_Params \
Option Creator Set parameters of Option before claim for it."total_amount_head" and "total_amount_tail" means amount of token. creator will swapping from "total_amount_head" head token to "total_amount_tail" tail token. "future_block_offset" indicates how many blocks until the option deal close.\
\
Interface:

        Set_Initializing_Params(uint256 total_amount_head ,uint256 total_amount_tail ,uint256 future_block_offset,string memory slogan)

- Claim_For_Head\
Option deal creator address pay token with address of "token_head" and claim for the option (HEAD side)\
\
Interface:

        Claim_For_Head() 


- Deposit_For_Tail\
 Any address pay ERC20 token with address of "token_tail" for the swap option (TAIL side). The  caller will get swapped token after the block where option close. Any swap after the option-close-block will get swapped token instantly. "amount" means that the caller spends amount tail token.The address "referer" referred this order to caller.\
 \
 Interface:
        
        Deposit_For_Tail(uint256 amount,address referer)


- Claim_For_Delivery\
 When the future is closed ,invoke this Method to claim token.Any swap after the option-close-block will get swapped token instantly.\
  \
Interface:
        
        Claim_For_Delivery()
- Withdraw_Head\
 If there is no rival, send tokens back and obliterate this deal.\
  \
Interface:

        Withdraw_Head() 

## Variables

- m_Amount_Head_Swapped: the amount of head token that has been swapped
- m_Amount_Tail_Swapped：the amount of tail token that has been swapped
- m_Amount_Head_Deliveryed: the amount of head token that has been deliveryed to tail side.
- m_Amount_Tail_Deliveryed: the amount of tail token that has been deliveryed to head side.

- m_Total_Amount_Head: how many head token the option creater send to this sub contract
- m_Total_Amount_Tail：how many tail token the option creater shall swap for.