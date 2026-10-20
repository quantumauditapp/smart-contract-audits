---
token: National Oil Dividend Fund🔥
ticker: NODF
network: base
risk_score: 65
status: high
date: 2026-10-20
---

# National Oil Dividend Fund🔥 (NODF) — Smart Contract Security Analysis | Base

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/national-oil-dividend-fund-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance, voting, and vesting capabilities. The architecture relies on a centralized owner to manage minting rates and pool transfer restrictions. While the code follows standard OpenZeppelin patterns, the high degree of administrative control presents a significant centralization risk to token holders.

> **Final Recommendation:** To improve security, transition ownership to a multi-signature wallet or a decentralized governance contract (DAO) to prevent single-point-of-failure risks. Implementing a timelock on sensitive functions like updateMintRate and pool management would provide transparency and allow users to react to administrative changes.

Ensure that all administrative actions are logged via events to maintain an audit trail. Consider renouncing ownership if the protocol reaches a state of maturity where active management is no longer required.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, voting, and permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner has unilateral control over token supply via updateMintRate and can halt liquidity via pool locking mechanisms. While these… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are straightforward, relying on the owner to trigger vesting releases and minting events. The lack of upgradeability… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to mint new tokens through the updateMintRate and release functions. This allows the owner to increase the total supply at their discretion, which can lead to the dilution of existing token holders' value.

**Recommendation:** Implement a timelock on the updateMintRate function or move the ownership to a multi-signature wallet to require consensus for supply changes.


### `CP-05` — Centralized Control Over Transfer Functionality  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to toggle a switch that determines whether transfers are allowed. This gives the owner the power to effectively freeze user funds or halt trading at any time.

**Recommendation:** Restrict the use of pool locking to emergency scenarios only and implement a decentralized governance mechanism to authorize such actions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.1% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,903 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,903 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $50K (DexScreener, all pools). 24h trading volume $311K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $50K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0cf5...8887`](https://basescan.org/address/0x0cf5974dc5f8339a27a61bd6075bff9245618887) |
| **Network** | Base |
| **Price** | $0.004957 |
| **24h Volume** | $310.7K |
| **Liquidity** | $49.9K |
| **Volume / Liquidity** | 6.2× |
| **Token Age** | 13h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3270 buys / 3213 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xe0f87ab989b6dfa00b2b260bbfa21215d592a5a34533ce9792b5eea1869ec5a6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/national-oil-dividend-fund-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
