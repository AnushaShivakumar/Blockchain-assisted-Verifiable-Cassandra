
# Blockchain-assisted Verifiable Cassandra

### Project Overview

The **Blockchain-assisted Verifiable Cassandra** project explores the intersection of blockchain technology and distributed databases. This proof-of-concept implementation focuses on securing data integrity for outsourced databases by integrating Merkle Hash Trees (MHT) and the Ethereum blockchain, providing verifiable and tamper-proof query results. By leveraging Cassandra as the primary database and incorporating blockchain for decentralized verification, the project aims to enhance trust in outsourced database services.

This project tackles the challenge of data tampering and untrusted database service providers by allowing clients to verify the authenticity of the queried data. Data owners upload their data to the service provider along with a Merkle Hash Tree, and the Merkle root is stored securely on the Ethereum blockchain. Query clients can use the Merkle proof to verify data authenticity by comparing it with the root stored on the blockchain.

### Key Entities
- **Data Owner (DO)**: The entity that prepares the dataset, constructs a Merkle Hash Tree, and uploads the data and MHT to the Service Provider. The Merkle root is stored on Ethereum.
- **Service Provider (SP)**: The outsourced database host (Cassandra) that stores the DO’s data and provides query responses along with Merkle proofs.
- **Query Client (C)**: The client requesting data and verifying its integrity using the Merkle proof and the Merkle root from Ethereum.
- **Malicious Client (MC)**: A simulated adversary attempting to tamper with the data in Cassandra, allowing the project to demonstrate how query verifications fail in case of tampered data.

### Project Features
1. **Data Integrity Verification**: Verifies the integrity of data using Merkle Trees. Clients can reconstruct the Merkle root from the Merkle proof provided by the Service Provider and compare it with the root stored on Ethereum.
2. **Blockchain Integration**: The Merkle root is stored on the Ethereum blockchain, ensuring decentralized, immutable, and tamper-resistant verification.
3. **Cassandra Database**: The Service Provider stores the data in a Cassandra database, which provides high availability and scalability for large datasets.
4. **Attack Simulation**: Simulates malicious tampering with the data, allowing the Query Client to detect and fail verification using the Merkle proof.

### Technologies Used
- **Cassandra Database**: A distributed NoSQL database for storing key-value pairs of the dataset.
- **Merkle Hash Tree (MHT)**: An Authenticated Data Structure (ADS) used to verify the integrity of the queried data.
- **Ethereum Blockchain**: Used to store the Merkle root on a smart contract, ensuring tamper-resistant verification.
- **Python**: The project is implemented in Python, with classes to simulate all entities (DO, SP, C, and MC).
- **Smart Contracts**: Ethereum smart contracts are used to store the Merkle root for verification.

### Project Workflow
1. **Data Preparation and MHT Construction**: The Data Owner (DO) prepares a dataset and builds a Merkle Hash Tree (MHT). The root of the MHT is stored on the Ethereum blockchain.
   
2. **Data Upload**: The DO uploads the dataset and the MHT to the Service Provider (SP), which stores the data in Cassandra.
   
3. **Query and Merkle Proof Generation**: The Query Client (C) sends a request to the SP for a key-value pair. The SP returns the queried data along with the Merkle proof.
   
4. **Verification**: The Query Client reconstructs the Merkle root using the Merkle proof and compares it with the root stored on the Ethereum blockchain. If the roots match, the data is verified; otherwise, the data is deemed tampered.
   
5. **Attack Simulation**: The Malicious Client (MC) tampers with the stored data in Cassandra. The Query Client can detect the tampering through failed verification.

### Components
- **Data Owner (DO)**: Constructs the MHT, uploads the data to the Service Provider, and stores the Merkle root on Ethereum.
- **Service Provider (SP)**: Hosts the Cassandra database and provides the Merkle proof for query verification.
- **Query Client (C)**: Sends requests to the SP and verifies the returned results using Merkle proofs and Ethereum.
- **Malicious Client (MC)**: Simulates data tampering to demonstrate the robustness of the verification system.
- **Ethereum Blockchain**: Stores the Merkle root for decentralized verification.

### Requirements
- Python 3.x
- Cassandra 3.x
- Ethereum development tools (e.g., Truffle, Ganache, Web3.py)
- Libraries: hashlib (for hashing), cassandra-driver (for interacting with Cassandra), web3.py (for Ethereum blockchain interaction)

### Running the Project
1. **Data Preparation**: The Data Owner prepares a key-value dataset and constructs the Merkle Hash Tree (MHT).
2. **Data Upload**: The Data Owner uploads the dataset to Cassandra and stores the Merkle root on the Ethereum blockchain.
3. **Query Request**: The Query Client sends a query request to the Service Provider for a key-value pair.
4. **Verification**: The Query Client verifies the query result by reconstructing the Merkle root using the Merkle proof and comparing it with the Merkle root stored on Ethereum.

### Usage Scenarios
- **Scenario 1: No Attack**: Run the system normally without tampering the data and show successful query verification.
- **Scenario 2: Attack Simulation**: Tamper with the data using the Malicious Client and demonstrate how query verification fails.

### Example Commands
1. **Prepare Data and Build MHT**:
   ```python
   python data_owner.py
   ```
2. **Upload Data to Cassandra**:
   ```bash
   python service_provider.py
   ```
3. **Run Query Client for Verification**:
   ```bash
   python query_client.py
   ```
4. **Simulate Attack**:
   ```bash
   python malicious_client.py
   ```
