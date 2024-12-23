# Jeremy AI CA: mzpo2uWEbRWJxMAg1r2kFqzQjofsGXAcCHoLtDqpump

An Algorithmic entity for connecting AI agents to Solana protocols. This project is manufactured in the Solana Agent Kit and aims to provide similar functionalities.

## Core Blockchain Features

- Token Operations
  - Deploy SPL tokens by Metaplex
  - Transfer assets
  - Balance checks
  - Stake SOL
  - Zk compressed Airdrop by Light Protocol and Helius

- NFT Management via Metaplex
  - Collection deployment
  - NFT minting
  - Metadata management
  - Royalty configuration

- DeFi Integration
  - Jupiter Exchange swaps
  - Launch on Pump via PumpPortal
  - Raydium pool creation (CPMM, CLMM, AMMv4)
  - Orca whirlpool integration
  - Meteora Dynamic AMM, DLMM Pool, and Alpga Vault
  - Openbook market creation
  - Register and Resolve SNS
  - Jito Bundles

- Solana Blinks
   - Lending by Lulo
   - Send Arcade Games
   - JupSOL staking

## AI Integration Features

- LangChain Integration
  - Ready-to-use LangChain tools for blockchain operations
  - Autonomous agent support with React framework
  - Memory management for persistent interactions
  - Streaming responses for real-time feedback

- Autonomous Modes
  - Interactive chat mode for guided operations
  - Autonomous mode for independent agent actions
  - Configurable action intervals
  - Built-in error handling and recovery

- AI Tools
  - DALL-E integration for NFT artwork generation
  - Natural language processing for blockchain commands
  - Price feed integration for market analysis
  - Automated decision-making capabilities

## Installation

```bash
npm install jeremy-ai

Quick Start

import { JeremyAI, createJeremyTools } from "jeremy-ai";

// Initialize with private key and optional RPC URL
const agent = new JeremyAI(
  "your-wallet-private-key-as-base58",
  "https://api.mainnet-beta.solana.com",
  "your-openai-api-key"
);

// Create LangChain tools
const tools = createJeremyTools(agent);

Usage Examples

Deploy a New Token

const result = await agent.deployToken(
  "my ai token", // name
  "uri", // uri
  "token", // symbol
  9, // decimals
  1000000 // initial supply
);

console.log("Token Mint Address:", result.mint.toString());

Create NFT Collection

const collection = await agent.deployCollection({
  name: "My NFT Collection",
  uri: "https://arweave.net/metadata.json",
  royaltyBasisPoints: 500, // 5%
  creators: [
    {
      address: "creator-wallet-address",
      percentage: 100,
    },
  ],
});

Swap Tokens

import { PublicKey } from "@solana/web3.js";

const signature = await agent.trade(
  new PublicKey("target-token-mint"),
  100, // amount
  new PublicKey("source-token-mint"),
  300 // 3% slippage
);

Lend Tokens

import { PublicKey } from "@solana/web3.js";

const signature = await agent.lendAssets(
  100 // amount of USDC to lend
);

Stake SOL

const signature = await agent.stake(
  1 // amount in SOL to stake
);

Send an SPL Token Airdrop via ZK Compression

import { PublicKey } from "@solana/web3.js";

(async () => {
  console.log(
    "~Airdrop cost estimate:",
    getAirdropCostEstimate(
      1000, // recipients
      30_000 // priority fee in lamports
    )
  );

  const signature = await agent.sendCompressedAirdrop(
    new PublicKey("JUPyiwrYJFskUPiHa7hkeR8VUtAeFoSYbKedZNsDvCN"), // mint
    42, // amount per recipient
    [
      new PublicKey("1nc1nerator11111111111111111111111111111111"),
      // ... add more recipients
    ],
    30_000 // priority fee in lamports
  );
})();

Fetch Price Data from Pyth

import { pythFetchPrice } from "jeremy-ai";

const price = await pythFetchPrice(
  agent,
  "0xe62df6c8b4a85fe1a67db44dc12de5db330f7ac66b72dc658afedf0f4a415b43"
);

console.log("Price in BTC/USD:", price);

API Reference
Core Functions
deploy_token(agent, decimals?, name, uri, symbol, initialSupply?)
Deploy a new SPL token with optional initial supply. If not specified, decimals default to 9.

deploy_collection(agent, options)
Create a new NFT collection with customizable metadata and royalties.

mintCollectionNFT(agent, collectionMint, metadata, recipient?)
Mint a new NFT as part of an existing collection.

transfer(agent, to, amount, mint?)
Transfer SOL or SPL tokens to a recipient.

trade(agent, outputMint, inputAmount, inputMint?, slippageBps?)
Swap tokens using Jupiter Exchange integration.

get_balance(agent, token_address)
Check SOL or token balance for the agent's wallet.

lendAsset(agent, assetMint, amount, apiKey)
Lend idle assets to earn interest with Lulo.

stakeWithJup(agent, amount)
Stake SOL with Jupiter to earn rewards.

sendCompressedAirdrop(agent, mintAddress, amount, recipients, priorityFeeInLamports?, shouldLog?)
Send an SPL token airdrop to many recipients at low cost via ZK Compression.

pythFetchPrice(agent, priceFeedID)
Fetch price data from Pyth's Hermes service.

Dependencies
The toolkit relies on several key Solana and Metaplex libraries:


