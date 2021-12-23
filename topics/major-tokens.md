# major tokens EIPs:

https://github.com/OpenZeppelin/openzeppelin-contracts/tree/master/contracts/token

## EIP-20
https://github.com/OpenZeppelin/openzeppelin-contracts/tree/master/contracts/token/ERC20

### Characteristics:
- 6 mains functions.
- 2 events
- Extensions:
   - burnable: burn tokens
   - capped: adds a cap to the supply of tokens
   - FlashMint: adds flash loans, default fees == 0
   - Pausable: preventing trades until the end of an evaluation period
   - Snapshot: the balances and total supply at the time are recorded for later access
   - Votes: support Compound-like voting and delegation (up to 2^224-1 VS 2^96-1)
   - VotesComp: exactly matches Compound's interface
   - Wrapper: support token wrapping. (if add too Vote -> governance token)
   - Metadata: name, symbol, decimal...
   - Permit: allowing approvals to be made via signatures


SafeERC20 : Tokens that return no value (and instead revert or throw on failure) are also supported
- Add some functions too:
   - safeIncreaseAllowance: safer than allowance because it risk of a user spending the old allowance and new one... It avoid to have to put allowance to 0 then to the new value.



### Skeleton of the smart contract:


pragma solidity ^0.8.0;

interface IERC20 {
    function totalSupply() external view returns (uint256);

    function balanceOf(address account) external view returns (uint256);

    function transfer(address recipient, uint256 amount) external returns (bool);

    function allowance(address owner, address spender) external view returns (uint256);

    function approve(address spender, uint256 amount) external returns (bool);

    function transferFrom(address sender, address recipient, uint256 amount) external returns (bool);

    event Transfer(address indexed from, address indexed to, uint256 value);
    event Approval(address indexed owner, address indexed spender, uint256 value);
}


## ERC721 - NFT
https://github.com/OpenZeppelin/openzeppelin-contracts/tree/master/contracts/token/ERC721

ERC721 is Context, ERC165, IERC721, IERC721Metadata
