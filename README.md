# Ex_No_3_Supply Chain Transparency for Luxury Goods
## Aim:
To develop a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
## Algorithm:
The manufacturer records product creation details on-chain.


The product moves through different supply chain checkpoints.


The ownership of the product can be transferred securely.


Buyers can verify the product’s authenticity.


## Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LuxurySupplyChain {
    struct Product {
        string name;
        address currentOwner;
        bool verified;
    }

    mapping(uint256 => Product) public products;

    event ProductRegistered(uint256 productId, string name);
    event OwnershipTransferred(uint256 productId, address newOwner);

    function registerProduct(uint256 productId, string memory name) public {
        require(products[productId].currentOwner == address(0), "Product already registered");
        products[productId] = Product(name, msg.sender, true);
        emit ProductRegistered(productId, name);
    }

    function transferOwnership(uint256 productId, address newOwner) public {
        require(products[productId].currentOwner == msg.sender, "Not the owner");
        products[productId].currentOwner = newOwner;
        emit OwnershipTransferred(productId, newOwner);
    }

    function verifyProduct(uint256 productId) public view returns (string memory, address, bool) {
        Product memory p = products[productId];
        return (p.name, p.currentOwner, p.verified);
    }
}
```
## Expected Output:
![WhatsApp Image 2026-02-12 at 9 36 57 AM](https://github.com/user-attachments/assets/f1b2cbaf-8086-482f-897b-a1bcee2c8236)

![WhatsApp Image 2026-02-12 at 9 36 57 AM (1)](https://github.com/user-attachments/assets/c88ec2a2-b185-4e62-bc76-3f643390f2d9)

Ownership is transferred at every checkpoint.


Buyers can check the authenticity before purchasing.


## High-Level Overview:
Helps prevent counterfeit luxury goods.


Teaches real-world supply chain use cases.

## RESULT : 
Thus a smart contract that tracks the supply chain of luxury goods, ensuring authenticity is executed successfully.
