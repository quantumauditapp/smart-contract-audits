---
token: XTO
ticker: XTO
network: base
risk_score: 63
status: medium
date: 2026-10-26
---

# XTO (XTO) — Smart Contract Security Analysis | Base

> **Risk Score: 63/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xto-base-7f5c)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with governance and vesting capabilities. The protocol exhibits centralized control, where the owner holds significant power over token supply and transferability. While the code follows standard OpenZeppelin patterns, the ability for the owner to unilaterally mint tokens and halt transfers presents a notable risk to token holders.

> **Final Recommendation:** To improve security and trust, consider transitioning ownership to a decentralized multi-signature wallet or a DAO governance contract. This would mitigate the risks associated with a single point of failure regarding minting and transfer control.

Additionally, implement a timelock mechanism for all privileged functions. A delay on actions like 'updateMintRate' or 'lockPool' would provide the community with sufficient notice and the ability to react to significant changes in tokenomics or transferability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to standard implementation… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are centralized. The owner can influence supply through minting and restrict liquidity via pool locking. While 7.6 External dependencies are minimal, the… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not implemented as this is a non-proxy contract. The logic is immutable, meaning the current privileged functions are fixed and cannot be removed without a full contract migration.… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Control  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to call 'updateMintRate' and 'release', which can increase the total supply of the token. This allows the owner to dilute the holdings of all existing token holders at their discretion.

**Recommendation:** Implement a hard cap on the total supply or transition the minting authority to a decentralized governance process with a timelock.


### `CP-05` — Centralized Transfer Control  *(Severity: Medium · Status: Unresolved)*

The owner can call 'lockPool' and 'unlockPool' to toggle the 'isPoolUnlocked' switch. This allows the owner to unilaterally prevent users from transferring their tokens, effectively freezing liquidity.

**Recommendation:** Remove the ability for the owner to pause or lock transfers, or restrict this functionality to emergency scenarios managed by a decentralized security council.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 96.2% in other contracts. 10 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

10 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $99K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x36dd...a5cd`](https://basescan.org/address/0x36dd1e8a94086ead257b1c6ced6293e37566a5cd) |
| **Network** | Base |
| **Price** | $0.00000724 |
| **24h Volume** | $98.9K |
| **Liquidity** | $11.7K |
| **Volume / Liquidity** | 8.4× |
| **Token Age** | 9h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1378 buys / 978 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xec23c5caa9061745474f4227935d846d63519cb3363a563ee8f3ceda1f286afa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xto-base-7f5c)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
