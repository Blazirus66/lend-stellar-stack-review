# User Flow & Capital Onboarding

The user journey on Stellar is designed to allow investors to participate in tokenized operations while enabling capital to flow into the ecosystem from both Stellar-native users and external blockchain networks.

## Investing with Stellar-native Assets

Users already holding **Stellar-native assets such as USDC** can directly participate in tokenized operations.

The process is straightforward:

1. The user connects a Stellar wallet.
2. The user selects a tokenized operation available on the platform.
3. The user invests in the operation.
4. The Factory contract mints **OpLend tokens** representing the investor's participation.

These tokens act as tokenized bonds corresponding to the investor’s share in the financing structure.

## Bridging Capital from Other Chains

In addition to native Stellar liquidity, the protocol aims to onboard capital from other blockchain ecosystems.

To achieve this, Lend plans to integrate bridging infrastructure allowing investors to bring assets from EVM chains into Stellar.

The current architecture considers using the **Allbridge API**, allowing users to:

1. Connect their Stellar wallet.
2. Detect available assets on external chains (and convert to USDC before bridging with li.fi).
3. Bridge USDC into the Stellar ecosystem.
4. Use the bridged assets to participate in tokenized operations.

This approach enables Lend to aggregate liquidity from multiple blockchain ecosystems while using Stellar as the settlement layer for tokenized real estate operations.

## Incentives for Stellar Adoption

To encourage liquidity and user activity on Stellar, Lend plans to allocate a **10% bonus in Lend Points generation** for investments executed on the Stellar instance of the protocol.

This incentive mechanism is designed to attract both existing Lend users and new investors, encouraging capital to flow into tokenized operations deployed on Stellar.
