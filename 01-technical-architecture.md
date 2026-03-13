# Technical Architecture

The Lend protocol on Stellar is built around a Soroban-based architecture designed to support compliant tokenized real-world asset financing.

The system relies on a **Factory contract** responsible for creating and managing tokenized investment operations. Each real estate financing opportunity is instantiated through this Factory, which deploys a dedicated **OpLend token** representing investor positions in the operation.

These tokens act as tokenized bonds where each fraction of a token corresponds to a share of the underlying financing structure. The Factory manages the lifecycle of operations, defines supply parameters, links metadata describing the asset and emits protocol events used by the indexing infrastructure.

## Backend Worker and Event Indexing

To synchronize on-chain activity with the application state, Lend operates a backend **worker system** responsible for indexing protocol events.

The worker continuously reads events emitted by the Factory and OpLend contracts through the **Soroban RPC `getEvents` endpoint**. These events are decoded and persisted into the platform database, allowing the system to reconstruct the full protocol state including:

- funding progress
- investor allocations
- token minting events
- operation lifecycle updates

The worker interacts with both **Soroban RPC** and **Horizon**.

Soroban RPC is used for:

- smart contract interaction
- transaction simulation
- event retrieval

Horizon provides complementary access to:

- account balances
- transaction history
- asset metadata
- network-level data

## Why Soroban Smart Contracts Instead of Native Stellar Assets

Although Stellar provides a native asset issuance model, Lend deliberately chose to implement tokenized operations through **Soroban smart contracts rather than Stellar native assets**.

While the native asset model offers simplicity and efficiency, the Soroban-based architecture allows the protocol to maintain full control over the token lifecycle and embed additional logic directly into the token contracts.

This approach enables:

- transfer restrictions
- compliance checks
- supply controls
- operation-specific logic
- protocol-level event emission

Using programmable contracts also ensures that the Factory remains the canonical entry point for all tokenized operations and preserves architectural consistency with the existing Lend protocol design.
