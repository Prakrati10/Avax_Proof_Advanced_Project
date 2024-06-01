# Avalanche Subnet

An avalanche subnet is a type of decentralized network architecture designed to facilitate secure and efficient data transmission. It operates on the Avalanche consensus protocol, which relies on a large number of validators, or nodes, to achieve consensus on the state of the network. In an avalanche subnet, nodes collaborate to reach agreement on transactions and maintain the integrity of the network without the need for a centralized authority. This approach enhances scalability, as the network can process a high volume of transactions in parallel, while also providing robust security through its consensus mechanism.

# Prerequisites

Before you begin, ensure you have the following tools and resources:

Unix computer (MacOS or Linux) or WSL installed on Windows
Remix online IDE
Metamask wallet extension
Web browser

# Project Implementation 

Set up your EVM subnet: To create a custom EVM subnet on the Avalanche network, follow the instructions provided in the guide and refer to the Avalanche documentation. This will allow you to deploy your smart contracts with low fees and create a custom token.

Define your native currency: Create your own native currency to serve as the in-game currency for your DeFi Kingdom clone. This currency will be used for transactions, rewards, and various in-game activities.

Connect to Metamask: To connect your EVM Subnet to Metamask, follow the instructions in the provided guide. Make sure to select your custom EVM subnet as the network in Metamask.

Deploy basic building blocks: To deploy foundational smart contracts for your game, you can leverage Solidity and Remix. These contracts will define activities such as battling, exploring, and trading. You can find example contracts in the provided guide.
1. ERC20 Token Contract
2. Vault Contract
   
Test your application: You can use Remix to interact with your deployed smart contracts for your DeFi Kingdom clone. With Remix, you can deploy tokens, liquidity pools, and other important components of your game. You can also test functionalities like battling, exploring, and trading within your game.

# ERC20 Token Contract 

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;

contract ERC20 {
    uint public totalSupply;
    mapping(address => uint) public balanceOf;
    mapping(address => mapping(address => uint)) public allowance;
    string public name = "Solidity by Example";
    string public symbol = "SOLBYEX";
    uint8 public decimals = 18;

		event Transfer(address indexed from, address indexed to, uint value);
    event Approval(address indexed owner, address indexed spender, uint value);

    function transfer(address recipient, uint amount) external returns (bool) {
        balanceOf[msg.sender] -= amount;
        balanceOf[recipient] += amount;
        emit Transfer(msg.sender, recipient, amount);
        return true;
    }

    function approve(address spender, uint amount) external returns (bool) {
        allowance[msg.sender][spender] = amount;
        emit Approval(msg.sender, spender, amount);
        return true;
    }

    function transferFrom(
        address sender,
        address recipient,
        uint amount
    ) external returns (bool) {
        allowance[sender][msg.sender] -= amount;
        balanceOf[sender] -= amount;
        balanceOf[recipient] += amount;
        emit Transfer(sender, recipient, amount);
        return true;
    }

    function mint(uint amount) external {
        balanceOf[msg.sender] += amount;
        totalSupply += amount;
        emit Transfer(address(0), msg.sender, amount);
    }

    function burn(uint amount) external {
        balanceOf[msg.sender] -= amount;
        totalSupply -= amount;
        emit Transfer(msg.sender, address(0), amount);
    }
}
```
1. The provided Solidity contract is an ERC20 token implementation.
2. It includes standard ERC20 functions such as transfer, approve, and transferFrom for token transfers and approvals.
3. The contract tracks the total token supply and individual balances using the totalSupply and balanceOf mappings.
4. It also manages allowances for delegated transfers using the allowance mapping.
5. The token has a name (Solidity by Example), symbol (SOLBYEX), and decimals (18).
6. Transfer events (Transfer) and approval events (Approval) are emitted upon relevant actions.
7. The transfer function allows users to transfer tokens to another address.
8. The approve function enables users to approve another address to spend tokens on their behalf.
9. The transferFrom function facilitates delegated transfers after approval has been granted.
10. The mint function allows the contract owner to create new tokens, increasing the total supply.
11. Conversely, the burn function enables token holders to destroy their tokens, decreasing the total supply.

# Advantages of Avalanche Subnet 

An Avalanche subnet is a decentralized network framework built upon the Avalanche consensus protocol, which employs a large network of nodes to achieve consensus on transaction validity and network state. Within this architecture, nodes cooperate to validate and propagate transactions across the network, enabling high throughput and low latency. Avalanche subnets operate without the need for a central authority, relying instead on a decentralized governance model to maintain network integrity and security. This approach fosters scalability and resilience, making Avalanche subnets suitable for a wide range of decentralized applications and digital asset ecosystems.
