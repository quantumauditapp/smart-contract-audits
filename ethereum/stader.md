---
token: Stader
ticker: SD
network: ethereum
risk_score: 49
status: medium
date: 2026-10-14
---

# Stader (SD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stader-eth)

---

## Audit Summary

The Stader contract is an ERC-20 token implementation with additional features for voting and permit functionality. The analysis found no privileged functions that could unilaterally control token transfers or modify critical contract state. No specific vulnerabilities were identified in the provided code map.

> **Final Recommendation:** Users should always exercise caution when interacting with any smart contract, verifying the contract address and understanding its intended functionality. While this audit found no specific vulnerabilities, general best practices such as using hardware wallets and understanding transaction details remain crucial. For developers, maintaining clear documentation and adhering to established standards for future integrations is recommended.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Stader contract implements a standard ERC-20 token with additional ERC-20 Permit, ERC-20 Votes, and ERC-20 Burnable functionalities (7.1 Architecture). The code adheres to established ERC… |
| **Governance / Economics** | 6/10 | Medium | The contract exhibits a strong governance and economic security posture due to the complete absence of privileged roles or centralized control mechanisms (7.5 Governance). Token transfers are solely… |
| **Upgrades** | 8/10 | Low | The Stader contract is not implemented as an upgradeable proxy (7.7 Upgrades). This means its logic is immutable once deployed, eliminating any risks associated with upgradeability, such as malicious… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x3352…bff8 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 52% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $160K (DexScreener, all pools). 24h trading volume $16.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $274K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $30.17 on 2022-03-15; the price is now 99.5249% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 74.1% of supply. Of that, 20.0% locked — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 37.9% in other contracts. 20,511 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Stader (SD), market cap $10M, rank #1208. Traded on Coinbase. 20,511 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Liquid Staking Governance Tokens. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $160K of DEX liquidity across 10 pools. Launch: 1675 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x30d2...d10f`](https://etherscan.io/address/0x30d20208d987713f46dfd34ef128bb16c404d10f) |
| **Network** | Ethereum |
| **Price** | $0.1408 |
| **24h Volume** | $70.9K |
| **Liquidity** | $83.4K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 4y |
| **Top-10 Holders** | 74.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 201 buys / 184 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xc3a55d8f14b35fa236dbb14ae1968e787f059bc03d43ed4ceabf25c589548fc5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stader-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-14*
