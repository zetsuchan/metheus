# Metheus

**Metheus** is an experimental, high-performance Layer 2 (L2) blockchain built in Rust. Inspired by cutting-edge projects like MegaETH, Metheus aims to push L2 performance toward hardware limits. Our goal is to deliver Web2-level throughput and real-time feedback loops while remaining EVM-compatible.

## Overview

- **Language**: Rust
- **Architecture**:
  - A specialized **Sequencer** node with multi-core, high-memory capacity (100+ cores, up to terabytes of RAM).
  - Lightweight **Prover** nodes (e.g., for optimistic or ZK proofs).
  - **Full Nodes** that apply state diffs and verify proofs without re-executing transactions.
- **Key Features**:
  1. **Ultra-Fast Execution**: Low-latency transaction processing with millisecond block times (configurable).
  2. **High Throughput**: Targeting thousands to hundreds of thousands of TPS by optimizing state access and parallel EVM (or custom execution).
  3. **EVM-Compatible**: Supports existing Ethereum tools and smart contracts.
  4. **Scalable Architecture**: Node specialization ensures that decentralized validation remains accessible while a powerful sequencer handles heavy lifting.

## Why Metheus?

Modern Ethereum-based L2s have shown impressive performance gains, but real-time blockchain use cases remain underexplored. Metheus focuses on:

1. **Multi-Terabyte Memory for State**  
   - Keep large portions of state in RAM for near-instant reads/writes, minimal disk I/O.
2. **High-Frequency Blocks**  
   - Sub-second or even 10ms block times to enable new dApps like real-time gaming or on-chain HFT.
3. **Holistic Optimization**  
   - Node specialization, improved state storage structures, parallel EVM, and more.

## Repository Structure

metheus/
├── core/
│   ├── executor/        # Rust-based transaction execution (EVM or custom VM)
│   ├── sequencer/       # Sequencer logic and block production
│   ├── prover/          # Prover logic (optimistic, ZK, or both)
│   └── fullnode/        # Full node implementation
│
├── config/
│   ├── genesis/         # Genesis files, initial allocations
│   ├── rollup.json      # Rollup or L2 configuration
│   └── network.toml     # Network parameters (gas, block time, etc.)
│
├── docs/                # Project documentation (whitepapers, specs)
├── scripts/             # Helper scripts (build, deploy, test)
├── tests/               # Integration tests
│
└── README.md            # This file

## Getting Started

### Prerequisites

- **Rust** (stable or nightly).  
- **cargo** (should come with Rust).
- **PostgreSQL** or another database (optional, depending on your storage driver).
- **git** for version control.

### Build & Run

1. **Clone the Repository**  
   ```bash
   git clone https://github.com/your-org/metheus.git
   cd metheus

	2.	Install Rust Toolchain

# If you haven't already
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
rustup default stable


	3.	Build the Project

cargo build --release

This will produce binaries under target/release/.

	4.	Run the Sequencer

./target/release/metheus-sequencer \
    --config config/rollup.json \
    --l1-rpc-url http://localhost:8545 \
    --block-time 50 \
    --memory-cache-size 128GB

	Adjust command-line flags to fit your environment (RAM size, block time, etc.).

	5.	Run a Full Node

./target/release/metheus-fullnode \
    --rollup-config config/rollup.json \
    --datadir /data/metheus/fullnode



Configuration

Metheus relies on configuration files in ./config/. Key parameters include:
	•	rollup.json: L2 chain ID, block gas limit, aggregator settings.
	•	network.toml: P2P layers, port settings, bandwidth constraints.
	•	genesis/: Genesis files for the L2 chain.

You can modify these to define:
	•	Block time
	•	Block gas limit
	•	Sequencer address
	•	Token economics
	•	Bridging & deposit contracts

Roadmap
	1.	MVP Execution + Sequencer
	•	Standalone L2 chain with basic block production.
	2.	Optimized State Storage
	•	In-memory tries or advanced data structures for minimal disk I/O.
	3.	Parallel EVM & JIT Compilation
	•	Speed up contract execution for compute-heavy transactions.
	4.	Node Specialization
	•	Expand Prover / Full Node roles, finalize trustless validation.
	5.	Real-Time Block Times
	•	Drive block times down to sub-second or even tens of milliseconds.
	6.	Bridging & Cross-Chain
	•	Integration with Ethereum mainnet or other L1s.
	7.	Production Launch
	•	Testing, audits, mainnet deployments.

Contributing

We welcome contributions from all backgrounds. To get started:
	1.	Fork this repo and create a new branch for your feature or bugfix.
	2.	Write clear, concise commit messages.
	3.	Submit a pull request (PR) detailing your changes.

Feel free to open an issue for discussion before coding:
	•	Feature Requests
	•	Bug Reports
	•	Documentation Improvements

License

Metheus is licensed under the Apache 2.0 License. See LICENSE file for details.

Disclaimer
	•	This project is experimental and not production-ready. Use at your own risk.
	•	Significant optimizations and audits are pending before mainnet release.

Happy Building!

If you have any questions, open an issue or reach out on our community channels. Let’s push blockchain performance to new heights together.


