---
token: CZ's Dog
ticker: BROWNIE
network: bsc
risk_score: 1
status: low
date: 2026-10-04
---

# CZ's Dog (BROWNIE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/czs-dog-bsc-b8ef)

---

## Audit Summary

This audit covers the Token contract, an ERC-20 standard token. The contract's ownership has been renounced, meaning no single entity can control its privileged functions. A single informational finding was identified, related to a dormant transfer control mechanism, which poses no active risk.

> **Final Recommendation:** For token holders, the renounced ownership significantly reduces centralized control risks, ensuring the contract's behavior is immutable. It is crucial to understand that while certain administrative functions exist in the code, they are permanently disabled. Future deployments of similar token contracts should carefully consider the necessity of administrative controls and, if required, implement robust, decentralized governance mechanisms rather than single-owner control to enhance long-term security and trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Token contract implements the ERC-20 standard, providing core functionalities like `transfer` and `transferFrom` (7.1 Architecture). The code appears straightforward and adheres to standard… |
| **Governance / Economics** | 10/10 | Low | The contract's economic model is based on the ERC-20 standard (7.4 Economic). Governance risks are significantly mitigated as the contract's ownership has been renounced on-chain (7.5 Governance).… |
| **Upgrades** | 10/10 | Low | The Token contract is a standard, non-upgradeable ERC-20 implementation. There are no proxy patterns or upgrade mechanisms present, which eliminates upgrade-related risks (7.7 Upgrades). This design… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 69.1% |
| **LP Locked** | 100.0% — Dead Address, GoPlus SafeToken Locker |

## Security Findings

_⚪ 6 Informational_

### `CP-05` — Dormant Transfer Control Switch  *(Severity: Informational · Status: Unresolved)*

The contract contains a function called `setMode` which, if active, would allow a privileged address (the owner) to change a setting (`_mode`) that could affect whether token transfers are allowed or blocked. However, the ownership of this contract has been permanently renounced. This means the `setMode` function can no longer be called by anyone, and the transfer control switch is permanently dormant.

**Recommendation:** As a token holder, you should be aware that while this control mechanism exists in the code, it cannot be activated or changed due to the renounced ownership. The current state of transfer rules is immutable. No action is required from token holders regarding this specific finding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 86.1% of supply. Of that, 32.6% burned, 33.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 18.2% in wallets, 1.3% in other contracts. 1,254 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,254 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 69.1% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 30.9% is locked in GoPlus SafeToken Locker until 10 Feb 2035 (3051 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $80K (DexScreener, all pools). 24h trading volume $608K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $80K of DEX liquidity across 1 pools. Launch: 598 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x556e...6108`](https://bscscan.com/address/0x556e0fea0bad640bc266a824e8b8a81dcc4c6108) |
| **Network** | BNB Chain |
| **Price** | $0.0002051 |
| **24h Volume** | $608.2K |
| **Liquidity** | $80.1K |
| **Volume / Liquidity** | 7.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 86.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1854 buys / 1679 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x63ff7cb4e90121d6f8c8c41e1a564c13a3c373a5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/czs-dog-bsc-b8ef)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*
