---
token: Zevio
ticker: ZEVIO
network: ethereum
risk_score: 6
status: low
date: 2026-10-08
---

# Zevio (ZEVIO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 6/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zevio-eth)

---

## Audit Summary

The LaunchToken contract is a standard ERC-20 token implementation. Static analysis indicates no privileged functions that can alter transfer logic or critical state, contributing to a low overall risk profile. No specific vulnerabilities were identified in the provided code map or prepared findings.

> **Final Recommendation:** For token holders, the LaunchToken contract appears to be a secure, standard ERC-20 implementation with no identified vulnerabilities or centralized control points. Users should always exercise caution when interacting with any smart contract, verifying the contract address and understanding the token's purpose within its broader ecosystem. Ensure that any platforms or dApps interacting with this token are also audited and trustworthy.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The LaunchToken contract implements the standard ERC-20 token interface, including `transfer`, `transferFrom`, and `approve` functions. Static analysis (7.2 Code Security) confirms no custom logic… |
| **Governance / Economics** | 7/10 | Low | The economic model of LaunchToken is straightforward, functioning as a basic ERC-20 token without complex fee structures or staking mechanisms (7.4 Economic). Crucially, there are no privileged roles… |
| **Upgrades** | 9/10 | Low | The LaunchToken contract is not implemented as an upgradeable proxy (7.7 Upgrades). This means its logic is immutable once deployed, eliminating risks associated with upgradeability, such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xd616…ad60 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 41% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 36.1% of supply. What remains: 4.8% in wallets, 31.3% in other contracts. 1,073 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,073 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $262K (DexScreener, all pools). 24h trading volume $1.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $262K of DEX liquidity across 20 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5df8...ae2b`](https://etherscan.io/address/0x5df882f8788071b67d0283f958ca3cdc17f1ae2b) |
| **Network** | Ethereum |
| **Price** | $0.0008048 |
| **24h Volume** | $791.2K |
| **Liquidity** | $106.4K |
| **Volume / Liquidity** | 7.4× |
| **Token Age** | 1d |
| **Top-10 Holders** | 36.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1207 buys / 1013 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x0a46bb6f6f18b986a622ac067b03d291515c81dba5bb7e9d6c8d6e033e14431d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zevio-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
