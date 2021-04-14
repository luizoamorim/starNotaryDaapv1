# Lesson Goals
In this lesson, we are going to build step by step two versions of the Star Notary Project;

- Star Notary Smart Contract Version 1 (Non-tokenized) - **Is this repo**
- Star Notary Smart Contract Version 2 (Tokenize)
- Learning Objectives
- Practice with the tools you need to create a DApp.
- Implement a Smart Contract to expose the DApp functionalities.
- Demonstrate how to test your Smart Contracts functionalities

# Tools, languages and libs
- Truffle
- Ganache
- VsCode
- Solidity
- JavaScript
- Web3
- Mocha
- Chai

# Mocha and Chai
- Mocha is a Testing Framework for Javascript, it can be used for front end applications and back end applications like Ethereum Decentralized Apps.
- Chai is an Assertion Library
- Both are available as NPM packages
- Very popular between developer for testing their code
- Truffle supports and comes preinstalled with Mocha and Chai

# Contract
We'll create a smart contract called StarNotary.sol

```
pragma solidity >=0.4.24;

contract StarNotary {

    string public starName;
    address public starOwner;

    event starClaimed(address owner);

    constructor() public {
        starName = "Awesome Udacity Star";
    }

    function claimStar() public {
        starOwner = msg.sender;
        emit starClaimed(msg.sender);
    }

}
```

To deploy this contract we need to create a migrate file 2_deploy_contracts.js:
```
const StarNotary = artifacts.require("StarNotary"); // Name of the StarNotary contract file

module.exports = function(deployer) {
  deployer.deploy(StarNotary);
};
```

# Test cases
- Create a file with a name starNotary.js in the test folder.
- This file is where we are going to write our tests cases.

# Run tests
- To run the test cases we need have the json compiled file.
- So let's run the follow commands:
```
truffle compile
truffle test 
```