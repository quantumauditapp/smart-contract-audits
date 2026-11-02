---
token: Kite
ticker: KITE
network: bsc
risk_score: 9
status: low
date: 2026-11-02
---

# Kite (KITE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kite-bsc)

---

## Audit Summary

The Kite contract is an Omnichain Fungible Token (OFT) implementation on BSC. It utilizes standard LayerZero integration for cross-chain transfers and includes administrative controls for pausing and cross-chain configuration. The protocol relies on a multisig owner, which mitigates single-point-of-failure risks, though the ability to mint tokens via cross-chain operations requires careful monitoring.

> **Final Recommendation:** The protocol should establish a clear, public policy regarding the minting of new tokens to maintain holder trust. Given the multisig setup, ensure that the signers are geographically and organizationally distributed to maximize the security of the administrative functions.

Regularly monitor the LayerZero endpoint configuration and the `enforcedOptions` state to ensure that cross-chain fees and gas limits remain aligned with network conditions. No immediate code changes are required, but active oversight of the owner-restricted functions is recommended.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows the standard LayerZero OFT pattern, ensuring robust cross-chain interoperability. 7.1 Architecture and 7.2 Code Security are well-implemented, utilizing established libraries… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance risks are centered on the owner's ability to influence token supply and transferability. The multisig requirement (4-of-6) provides a strong governance layer against… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades and 7.8 Operations are currently static as the contract is not a proxy. The protocol does not support self-upgradability, which eliminates risks associated with implementation swaps.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.4% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 6 Informational_

### `CP-01` — Privileged Minting Capability  *(Severity: Informational · Status: Unresolved)*

The contract allows for the creation of new tokens through the `send`, `lzReceiveSimulate`, and `lzReceive` functions. This mechanism is necessary for cross-chain functionality but effectively allows the protocol to increase the total supply, which can dilute the value of existing holdings.

**Recommendation:** Maintain strict transparency regarding the total supply and ensure that cross-chain minting parameters are audited and monitored for anomalies.


### `CP-04` — Centralized Pause Control  *(Severity: Informational · Status: Unresolved)*

The owner has the authority to call `pause` and `unpause`, which halts all token transfers. This centralized control acts as a kill-switch that can prevent users from moving their assets during an emergency or if the owner's keys are compromised.

**Recommendation:** Consider implementing a time-lock on the pause functionality or transitioning to a decentralized governance model to reduce reliance on the multisig owner.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 87.5% of supply. What remains: 51.0% in wallets, 36.5% in other contracts. 9,770 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Kite (KITE), market cap $290M, rank #138. Traded on Coinbase. 9,770 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.6M (GeckoTerminal, all pools). 24h trading volume $13.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $839K (GeckoTerminal, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: a copy of the coin from its home chain (ethereum), minted here by LayerZero (lzReceive). Tokenomics — Supply: minted here by LayerZero (lzReceive) against tokens locked or burned on other chains. Control: a 4-of-6 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.6M of DEX liquidity across 20 pools. Launch: 365 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9045...16be`](https://bscscan.com/address/0x904567252d8f48555b7447c67dca23f0372e16be) |
| **Network** | BNB Chain |
| **Price** | $0.11476563 |
| **24h Volume** | $839.5K |
| **Liquidity** | $1.55M |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 87.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3027 buys / 3439 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x904567252d8f48555b7447c67dca23f0372e16be)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kite-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
