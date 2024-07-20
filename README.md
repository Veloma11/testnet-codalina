# testnet-codalina
Testnet name is Codaline. Testnet token is coda
npm install --save-dev hardhat

Hardhat:
mkdir codaline-project
cd codaline-project
npx hardhat

// contracts/MyContract.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyContract {
    string public message;

    constructor(string memory _message) {
        message = _message;
    }

    function setMessage(string memory _message) public {
        message = _message;
    }
}


require("@nomiclabs/hardhat-waffle");

module.exports = {
  solidity: "0.8.0",
  networks: {
    codaline: {
      url: "https://codaline-testnet-url", // Замените на фактический URL тестовой сети Codaline
      accounts: ["0x..."] // Замените на ваш приватный ключ
    }
  }
};
// scripts/deploy.js
async function main() {
  const [deployer] = await ethers.getSigners();

  console.log("Deploying contracts with the account:", deployer.address);

  const MyContract = await ethers.getContractFactory("MyContract");
  const myContract = await MyContract.deploy("Hello, Codaline!");

  console.log("MyContract deployed to:", myContract.address);
}

main()
  .then(() => process.exit(0))
  .catch(error => {
    console.error(error);
    process.exit(1);
  });
npx hardhat run scripts/deploy.js --network codaline
