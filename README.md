# CVIN_2024
Repository for CVIN smart contract implementations, scenarios, and testing suites.

CVIN Identity Systems.
Overview
This repository contains implementations of ERC721 and ERC725 smart contracts. These implementations are part of a research thesis on building a suitable Self-Sovereign Identity (SSI) for Connected and Autonomous Vehicles (CAVs) and infrastructure, forming the Internet of Vehicles (IoV). The work explores the application of digital identities and identity systems to machines, particularly CAVs, to enable secure communication, verification of identities, and associated information.

Abstract (Extended)
Digital identities and identity systems are being applied to many fields, including for machines in general as well as Connected and Autonomous Vehicles (CAVs), and are proving to be valuable to enable secure communication, and verification of identities or associated information. Furthermore, digital identities enable secure data exchange and interoperability among various systems and devices, which is critical for the efficient functioning of CAVs. The leading paradigm and standards for building secure identities and supporting infrastructure is tending towards blockchain-based and Self-Sovereign Identity (SSI); where decentralized infrastructure and networks such as blockchains and distributed ledgers are used to build identity systems with primary building blocks of Decentralized Identities (DIDs), the associated data with identities known as Verifiable Credentials (VCs), and security algorithms and protocols such as encryption, signing of messages, and selective disclosure of information. Despite this, no work has been done on the convergence of SSI, CAVs, current decentralized networks, and blockchains, let alone benchmarking and stress testing of the various paradigms of implementing such systems via smart contracts - or at least anchored to them in some manner.

Directory Structure
ERC721/: Contains the ERC721 smart contract implementation.
contracts/: The smart contract code.
scripts/: The deployment scripts.
test/: The test scripts.
README.md: Instructions for ERC721 contract.
ERC725/: Contains the ERC725 smart contract implementation.
contracts/: The smart contract code.
scripts/: The deployment scripts.
test/: The test scripts, including generic and scenario-based tests.
README.md: Instructions for ERC725 contract.
README.md: General overview of the repository.
Setting Up with Hardhat
Prerequisites
Node.js (v14 or higher)
Hardhat
Installation
Clone the repository:

bash
Copy code
git clone https://github.com/YOUR_GITHUB_USERNAME/ERC_Smart_Contracts.git
cd ERC_Smart_Contracts
Install dependencies:

bash
Copy code
npm install
Compilation
Compile the smart contracts:

bash
Copy code
npx hardhat compile
Deployment
Deploy the smart contracts to a local network:

Create a deployment script scripts/deploy.js for each contract. Example for ERC725:

javascript
Copy code
const hre = require("hardhat");

async function main() {
    const [deployer] = await hre.ethers.getSigners();

    console.log("Deploying contracts with the account:", deployer.address);

    const CVIN_SCBasedAccOrID = await hre.ethers.getContractFactory("CVIN_SCBasedAccOrID_DID_ERC725Basic_Monolithic");
    const cvin_sc_based_acc_or_id = await CVIN_SCBasedAccOrID.deploy();

    await cvin_sc_based_acc_or_id.deployed();

    console.log("CVIN_SCBasedAccOrID deployed to:", cvin_sc_based_acc_or_id.address);
}

main()
    .then(() => process.exit(0))
    .catch((error) => {
        console.error(error);
        process.exit(1);
    });
Run the deployment script:

bash
Copy code
npx hardhat run scripts/deploy.js --network localhost
Testing
Run Various Testing Suites for Each Implementation"
E.g. Test Suite #1: Generic Testing, and Test Suite #2: Basic CAV VID Scenario Testing, ...
Run the generic test suite:

bash
Copy code
npx hardhat test test/generic.js
Run the scenario-based test suite:

bash
Copy code
npx hardhat test test/scenario.js

