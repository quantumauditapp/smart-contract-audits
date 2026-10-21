---
token: RLUSD
ticker: RLUSD
network: ethereum
risk_score: 11
status: low
date: 2026-10-21
---

# RLUSD (RLUSD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 11/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/rlusd-eth)

---

## Audit Summary

The protocol implements a centralized stablecoin with robust administrative controls, including minting, burning (clawback), and account-level pausing. The architecture utilizes a UUPS proxy pattern for upgradability. No critical or high-severity vulnerabilities were identified during the static analysis of the provided contract logic.

> **Final Recommendation:** The protocol is well-structured and follows secure development patterns. It is recommended to implement a multi-signature wallet or a timelock controller for all administrative roles to mitigate the risk of a single compromised key performing unauthorized minting or clawback actions.

Ensure that the private keys for the MINTER_ROLE, CLAWBACKER_ROLE, and PAUSER_ROLE are stored in a secure, offline environment (e.g., hardware security modules) to maintain the integrity of the token supply and user account status.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The architecture follows standard OpenZeppelin patterns for ERC-20 and AccessControl, ensuring 7.1 Architecture and 7.2 Code Security standards are met. 7.3 Access Control is strictly enforced via… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance risks are inherent to the centralized nature of the token. The ability for privileged roles to mint and clawback tokens represents a significant trust requirement for… |
| **Upgrades** | 5/10 | Medium | The protocol utilizes the UUPS proxy pattern (7.7 Upgrades), which is the current industry standard for gas-efficient and secure upgrades. The implementation contract is correctly linked to the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 50.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 68.4% of supply. What remains: 40.8% in wallets, 27.6% in other contracts. 12,847 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Ripple USD (RLUSD), market cap $2.4B, rank #43. 12,847 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $103.1M (DexScreener, all pools). 24h trading volume $167.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $27.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply; pause all transfers. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Stablecoin — issuer-backed (fiat reserves)  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Fiat-backed Stablecoin. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $103.1M of DEX liquidity across 10 pools. Launch: 671 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8292...17ed`](https://etherscan.io/address/0x8292bb45bf1ee4d140127049757c2e0ff06317ed) |
| **Network** | Ethereum |
| **Price** | $1.0008 |
| **24h Volume** | $21.79M |
| **Liquidity** | $50.04M |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 68.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 61 buys / 53 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x9035721b23481db3888fd201b9c2b26dbc3af60258bca65e669f2ed98dc8eb4f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/rlusd-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
