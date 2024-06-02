# REMIX-Etherium-IDE-Solidity-Assessment

"This little Solidity Program is like a basic checklist for what we need in our contract. It's got some stuff everyone can see, some behind-the-scenes things, and even functions to create and destroy tokens in our contract."

## Description

"This program is like a basic agreement written in Solidity, a language used for making smart contracts on Ethereum. It's all about managing a digital coin.

In our contract, we'll have some public details about the coin, like its name, abbreviation, and how much of it exists overall.

We'll keep track of who has how much of our coin using a special list that matches addresses to balances, kind of like a digital wallet.

Now, onto the cool functions: First, there's 'mint'. It's like a coin-making button. You tell it where to send the new coins and how many to make, and it does the job. Simple, right?

Then there's 'burn'. This one's like a coin-destroying button. You give it an address and an amount, and it takes those coins out of circulation. Poof! They're gone.

But hey, we've got to make sure people aren't burning coins they don't have. So, our burn function double-checks to ensure the sender actually has enough coins to burn.

In a nutshell, this program is like a rulebook for our digital coin, keeping everything fair and square."

## Getting Started

### Executing program

"To try out this program, you can use Remix, which is like an online tool for writing and testing Solidity code. Here's how to get started:

Go to the Remix website by clicking this link: [Remix Website](https://remix.ethereum.org/#lang=en&optimize=false&runs=200&evmVersion=null&version=soljson-v0.8.18+commit.87f61d96.js)

Once you're on the Remix website, look for a little "+" sign on the left side and click on it. This will create a new file.

Save the file with a name and make sure it ends with .sol (like MyToken.sol).

Now, copy and paste the code we provided into the file.

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyToken {
    // State variables
    string public tokenName = "Keith";
    string public tokenAbbrv = "Christian";
    uint256 public totalSupply;
    mapping(address => uint256) public balance;

    // Events
    event Transfer(address indexed from, address indexed to, uint256 value);
    event Mint(address indexed to, uint256 value);
    event Burn(address indexed from, uint256 value);

    // Constructor
    constructor() {
        // Initial supply is 0
        totalSupply = 0;
    }

    // Mint tokens and assign to an address
    function mint(address _to, uint256 _value) public {
        totalSupply += _value;
        balance[_to] += _value;
        emit Mint(_to, _value);
        emit Transfer(address(0), _to, _value);
    }

    // Burn tokens from a specific address
    function burn(address _from, uint256 _value) public {
        require(balance[_from] >= _value, "Insufficient balance");
        totalSupply -= _value;
        balance[_from] -= _value;
        emit Burn(_from, _value);
        emit Transfer(_from, address(0), _value);
    }

    // Transfer tokens from sender to another address
    function transfer(address _to, uint256 _value) public {
        require(balance[msg.sender] >= _value, "Insufficient balance");
        balance[msg.sender] -= _value;
        balance[_to] += _value;
        emit Transfer(msg.sender, _to, _value);
    }

    // Get the balance of an address
    function balanceOf(address _owner) public view returns (uint256) {
        return balance[_owner];
    }
}

```
"To get started, let's compile the code. Click on the 'Solidity Compiler' tab on the left-hand side of the screen. Make sure the 'Compiler' option is set to '0.8.18' (or another version that works), and then hit the 'Compile MyToken.sol' button.

Once the code is compiled, it's time to deploy the contract. Click on the 'Deploy & Run Transactions' tab in the sidebar. Choose 'MyToken' from the dropdown menu, and then click 'Deploy'.

After the contract is deployed, you'll see an account at the top of the page. Click 'Copy Account' on the left side to copy it.

Now, let's mint some tokens. Press the downward arrow next to 'Mint' and paste the copied account into the 'Address' field. Type '1000' into the 'Value' field and click 'Transact'.

Next, let's burn some tokens. Press the downward arrow next to 'Burn', paste the copied account into the 'Address' field, and type '500' into the 'Value' field.

To check the total supply, scroll to the bottom and click on 'Total Supply'. You'll see '500' appear in the 'uint'. And that's it, you're done!"
## Authors

Christian Keith Arreglo BSIT 
@keithmaster07

# License

Copyright (c) 2024 keithmaster07

