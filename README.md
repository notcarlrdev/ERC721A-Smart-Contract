<h1 align="center" id="title">ERC721A Smart Contract ( modified )</h1>

<p align="center"><img src="https://img.shields.io/github/last-commit/bogartph2022/ERC721A-Smart-Contract" alt="shields"></p> | <p align=><img src="https://img.shields.io/github/forks/bogartph2022/ERC721A-Smart-Contract?style=social" alt="shields"></p>

  
  
<h2>🧐 Features</h2>

Here're some of the project's best features:

*   Bulk address minting / airdrop
*   Lower gas fees
*   Opening and closing minting
*   And many more

<h2>🛠️ Editing Smart Contract</h2>

<b>Creating Your Contract Metadata. ( contract_metadata.json )</b>

```
{   
    "name": "Your Collection Name"   
    "description": "Your Collection Description"   
    "seller_fee_basis_points": 2.5 // You can always change this configuration  
    "external_link": "https://YourWebsiteName.com"   
    "fee_recipient": "Your Wallet Address" 
}
```

<b>Changing baseURI</b>

```
function _baseURI() internal view virtual returns (string memory) {     
    return "Your Base URI Here";   
}
```

<b>Changing Minting Price and baseTokenURI</B>

```
abstract contract BogartERC721A is 
    Ownable,
    ERC721A,
    Withdrawable,
    ReentrancyGuard  {
    constructor(
        string memory tokenName,
        string memory tokenSymbol
    ) ERC721A(tokenName, tokenSymbol, 2, 5000 ) {}
    using SafeMath for uint256;
    uint8 public CONTRACT_VERSION = 2;
    string public _baseTokenURI = "Your Base URI";

    bool public mintingOpen = true;
    
    uint256 public PRICE = MintingPrice ether;
```

<b>Changing Collection name, Token Symbol, and Contract Metadata URL</b>

```
pragma solidity ^0.8.0;

contract CollectionNAme is BogartERC721A {
    constructor() BogartERC721A("Your Collection Name", "SYMBOL"){}

    function contractURI() public pure returns (string memory) {
      return "https://ipfs.io/YourIpfsCID";
    }
}
```

<b>Changing My Wallet address that can access withdraw funds from smart contract</b>

```
abstract contract BogartWallet {
  address public BOGARTADDRESS = 0x9E16599F96811ea8Be59B3f4ae03308f6DA9e5A0;

  modifier isBogart() {
      require(msg.sender == BOGARTADDRESS, "Ownable: caller is not Dev Bogart");
      _;
  }
}
```

<b>Editing payableWalletAddress</b>

```
abstract contract Withdrawable is Ownable, BogartWallet {
  address[] public payableAddresses = [BOGARTADDRESS,0x9E16599F96811ea8Be59B3f4ae03308f6DA9e5A0];
  uint256[] public payableFees = [5,95];
  uint256 public payableAddressCount = 2;
```

<h2>⚠️ Warning</h2>

After deploying this contract in remix, please do all the configurations before exiting or refreshing the page. You can also verify this contract in Etherscan so you can always make configurations.

<h2>🍰 Creators and modifiers:</h2>

This ERC721A Contract was made by chiru labs and was modified by Bogart#0001

<h2>🛡️ License:</h2>

This project is licensed under the MIT License

<h2>💖Like my work?</h2>

Message me in discord <b>Bogart#0001</b> if you need a ERC721A Contract Deployer or you have any questions.
