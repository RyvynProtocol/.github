# RYVYN Protocol

<div align="center">

**A revolutionary stablecoin platform that rewards users on every transfer with real-world asset-backed yields.**

[![Frontend](https://img.shields.io/badge/Frontend-Next.js%2015-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![Smart Contracts](https://img.shields.io/badge/Smart%20Contracts-Solidity-363636?style=for-the-badge&logo=solidity)](https://soliditylang.org/)
[![Network](https://img.shields.io/badge/Network-Mantle%20Sepolia-blue?style=for-the-badge)](https://www.mantle.xyz/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

</div>

---

## 📖 Overview

RYVYN Protocol is a decentralized yield-bearing stablecoin protocol built on Ethereum. Users can deposit USDC to mint **ryUSD** (Ryvyn USD) and earn passive yield through **ryBOND** rewards.

### Core Components

- **ryUSD**: A 1:1 USDC-backed stablecoin with 6 decimals
- **ryBOND**: A yield reward token with built-in vesting (7 days by default)
- **Treasury Management**: Automated allocation of deposited funds across multiple yield strategies
- **Dynamic Rewards**: Activity-based reward distribution using token bucket mechanics

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🏦 **Real World Assets** | Treasury backed by 60% US T-Bills and 25% Corporate Bonds, turning idle money into working capital |
| 💸 **Profitable Payments** | Gamified investment with deterministic rewards on every transaction, split between sender and receiver |
| 🌊 **Stream Bonds (ryBOND)** | Sustainable yield that streams over time, claim your yield as it drips every second |
| 🪙 **ryUSD Stablecoin** | Mint and transfer the protocol's native stablecoin |
| 📊 **Treasury Dashboard** | Real-time visibility into asset allocation and yields |
| 📜 **Transaction History** | Complete transaction log with rewards tracking |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                         User Actions                            │
│              (deposit USDC / withdraw / transfer)               │
└───────────────────────────────┬─────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                           ryUSD                                 │
│                (ERC20 Stablecoin - 1:1 USDC)                    │
└──────────────┬─────────────────────────────────┬────────────────┘
               │                                 │
               ▼                                 ▼
┌──────────────────────────────┐  ┌──────────────────────────────┐
│     TreasuryManager          │  │       RyvynHandler           │
│   (Fund Allocation)          │  │    (Reward Calculation)      │
│                              │  │                              │
│  ┌────────────────────┐      │  │   ┌─────────────────────┐    │
│  │   Strategies:      │      │  │   │   Token Buckets     │    │
│  │ • 40% USDY         │      │  │   │   (Age Tracking)    │    │
│  │ • 30% OUSG         │      │  │   └─────────────────────┘    │
│  │ • 20% Lending      │      │  │              │               │
│  │ • 10% Reserve      │      │  │              ▼               │
│  └────────────────────┘      │  │   ┌─────────────────────┐    │
└──────────────────────────────┘  │   │   YieldManager      │    │
               │                  │   │ (Dynamic Rewards)   │    │
               │                  │   └─────────────────────┘    │
               │                  └──────────────┬───────────────┘
               │                                 │
               ▼                                 ▼
┌─────────────────────────────────────────────────────────────────┐
│                          ryBOND                                 │
│                 (Vested Yield Rewards)                          │
│              - Locked → Vested → Claimable                      │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📦 Repositories

| Repository | Description | Tech Stack |
|------------|-------------|------------|
| **[FE](https://github.com/RyvynProtocol/FE)** | Frontend Application | Next.js 15, TypeScript, Tailwind CSS 4.0, Wagmi, Privy |
| **[SC](https://github.com/RyvynProtocol/SC)** | Smart Contracts | Solidity, Foundry |

---

## 🚀 Deployment Instructions

### Smart Contracts

**Network: Mantle Testnet Sepolia**

| Parameter | Value |
|-----------|-------|
| RPC URL | `https://rpc.sepolia.mantle.xyz` |
| Chain ID | `5003` |
| Explorer | `https://sepolia.mantlescan.xyz` |

```bash
# Clone the repository
git clone https://github.com/RyvynProtocol/SC.git
cd SC

# Install dependencies
forge install

# Build contracts
forge build

# Run tests
forge test

# Deploy to Mantle Sepolia
forge script script/Deploy.s.sol:DeployScript \
  --rpc-url https://rpc.sepolia.mantle.xyz \
  --private-key <your_private_key> \
  --broadcast
```

### Frontend

```bash
# Clone the repository
git clone https://github.com/RyvynProtocol/FE.git
cd FE

# Install dependencies
pnpm install

# Run development server
pnpm dev

# Build for production
pnpm build

# Start production server
pnpm start
```

Open [http://localhost:3000](http://localhost:3000) to view the application.

---

## 📁 Project Structure

### Smart Contracts (SC)

```
src/
├── core/
│   ├── ryUSD.sol           # Stablecoin contract
│   ├── ryBOND.sol          # Yield reward contract
│   └── RyvynHandler.sol    # Core handler logic
├── treasury/
│   ├── TreasuryManager.sol # Fund allocation
│   └── YieldManager.sol    # Yield pool management
├── interfaces/             # Contract interfaces
├── logic/
│   └── TokenBucketLib.sol  # Token bucket library
└── mocks/                  # Mock contracts for testing
```

### Frontend (FE)

```
src/
├── abis/           # Smart contract ABIs
├── app/            # Next.js App Router pages
├── components/     # Reusable UI components
├── config/         # App configuration
├── features/       # Feature-specific components
├── hooks/          # Custom React hooks
├── lib/            # Utility functions
├── providers/      # React context providers
└── types/          # TypeScript type definitions
```

---

## 🛠️ Tech Stack

### Frontend
| Category | Technologies |
|----------|--------------|
| **Framework** | Next.js 15 with App Router & Turbopack |
| **Language** | TypeScript |
| **Styling** | Tailwind CSS 4.0 |
| **Web3 Auth** | Privy |
| **Blockchain** | Wagmi, Viem |
| **Animations** | Motion (Framer Motion) |
| **3D Graphics** | Three.js, OGL |
| **Charts** | Recharts |
| **UI Components** | Radix UI, Lucide React |

### Smart Contracts
| Category | Technologies |
|----------|--------------|
| **Language** | Solidity |
| **Framework** | Foundry |
| **Testing** | Forge |
| **Network** | Mantle Sepolia |

---

## 📄 License

This project is licensed under the MIT License.

---

## ⚠️ Security

> **Warning**: This protocol is under active development. Use at your own risk. Smart contracts have not been audited.

---

<div align="center">

Built with ❤️ by the RYVYN Team

</div>