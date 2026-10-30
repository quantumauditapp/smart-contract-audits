---
token: Wootrade Network
ticker: WOO
network: arbitrum
risk_score: 17
status: low
date: 2026-10-30
---

# Wootrade Network (WOO) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wootrade-network-arb)

---

## Audit Summary

The protocol implements a standard Arbitrum L2 gateway token pattern using a beacon proxy architecture. The contract relies on external gateway contracts to manage minting and burning operations. While the implementation follows established L2 standards, the centralization of power within the gateway contract poses a significant risk to token holders.

> **Final Recommendation:** Token holders should be aware that the bridge gateway contract holds absolute authority over token supply and individual balances. It is recommended to monitor the gateway contract for any administrative changes or security updates.

Ensure that the multisig or governance mechanism controlling the bridge gateway is robust, as this is the single point of failure for the entire token ecosystem.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The architecture utilizes a standard beacon proxy pattern, ensuring consistent implementation across clones (7.1 Architecture). Code security is high, leveraging audited OpenZeppelin upgradeable… |
| **Governance / Economics** | 9/10 | Low | Economic stability is maintained by the bridge gateway, which acts as the sole source of truth for supply (7.4 Economic). Governance is currently centralized within the bridge infrastructure, lacking… |
| **Upgrades** | 5/10 | Medium | The protocol uses a beacon proxy pattern, allowing for efficient upgrades across multiple instances (7.7 Upgrades). Operational security is maintained through standard proxy management practices (7.8… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 53.2% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $271K (GeckoTerminal, all pools). 24h trading volume $1.9M (CoinGecko, all markets, daily snapshot). 24h trading volume $36K (GeckoTerminal, all pools). CoinGecko's record for this coin: all-time high $1.78 on 2021-11-15; the price is now 99.455% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `CP-01` — Privileged Minting Capability  *(Severity: Informational · Status: Unresolved)*

The bridgeMint function allows the authorized gateway address to increase the total supply of the token at any time, which can lead to the dilution of existing token holders' value.

**Recommendation:** Ensure the gateway contract is governed by a secure, multi-signature wallet or a decentralized governance process to prevent unauthorized minting.


### `CP-02` — Privileged Balance Manipulation  *(Severity: Informational · Status: Unresolved)*

The bridgeBurn function allows the authorized gateway address to directly remove tokens from any user's balance, effectively granting the gateway controller the ability to seize or destroy user funds.

**Recommendation:** Implement strict timelocks or multi-signature requirements for any actions that involve burning tokens from user addresses to prevent potential abuse.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The holder list from the security indexer adds up to 104.6% of supply, so it does not describe real balances. That happens with rebasing and reflection tokens, whose balances change without transfers, and with contracts that report balances they do not hold. Concentration is unknown and priced as an unknown — neither a whale nor safe.

**Recommendation:** Check the largest holders on the block explorer, which reads current balances.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as WOO (WOO), market cap $18M, rank #887. On GoPlus's list of trusted tokens. Traded on Binance. 49,798 holders. Verified by: CoinGecko, GoPlus, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: a copy of the coin from its home chain (ethereum), minted here by the chain's standard bridge (bridgeMint). Tokenomics — Supply: minted here by the chain's standard bridge (bridgeMint) against tokens locked or burned on other chains. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $271K of DEX liquidity across 20 pools. Launch: 1462 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcafc...d07b`](https://arbiscan.io/address/0xcafcd85d8ca7ad1e1c6f82f651fa15e33aefd07b) |
| **Network** | Arbitrum |
| **Price** | $0.00967556 |
| **24h Volume** | $35.5K |
| **Liquidity** | $252.6K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 4y |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 180 buys / 173 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0xcafcd85d8ca7ad1e1c6f82f651fa15e33aefd07b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wootrade-network-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
