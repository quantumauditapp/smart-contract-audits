---
token: USDP
ticker: USDP
network: base
risk_score: 57
status: medium
date: 2026-10-25
---

# USDP (USDP) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usdp-base-27ee)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The architecture relies heavily on a centralized owner account, which possesses significant control over token supply and transferability. While the code follows standard OpenZeppelin patterns, the centralization of power presents a notable risk to token holders.

> **Final Recommendation:** To improve security, consider transitioning the ownership to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single compromised key. Additionally, implementing a timelock on sensitive functions like updateMintRate would provide the community with visibility and time to react to significant economic changes.

Ensure that all administrative actions are logged and monitored. Given the current centralization, users should be aware that the owner has the technical capability to influence token supply and liquidity access.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-tested OpenZeppelin libraries for ERC-20 and governance features. 7.1 Architecture is modular, and 7.2 Code Security is high due to standard implementation patterns. 7.3… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the owner. The owner can unilaterally mint tokens and halt transfers, which directly impacts 7.4 Economic stability. These powers… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable, which provides security against unauthorized logic changes but prevents patching if a vulnerability is… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Control  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to increase the total supply of the token via the updateMintRate and release functions. This allows the owner to dilute the holdings of all existing token holders at their discretion.

**Recommendation:** Implement a timelock for minting operations or transition ownership to a DAO to ensure community oversight of supply changes.


### `CP-05` — Centralized Transfer Control  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch via the lockPool and unlockPool functions. This allows the owner to unilaterally freeze or unfreeze token transfers, effectively controlling the liquidity of the token.

**Recommendation:** Remove the ability to pause transfers or restrict this functionality to a decentralized governance mechanism to prevent arbitrary censorship of user transactions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,080 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,080 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $460K (DexScreener, all pools). 24h trading volume $664K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.9429 — it does not hold a peg. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $460K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9aed...73c5`](https://basescan.org/address/0x9aed361a6513a35850ade972ceb515172d3173c5) |
| **Network** | Base |
| **Price** | $0.9429 |
| **24h Volume** | $664.3K |
| **Liquidity** | $459.5K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 13h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1392 buys / 1367 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xba97f378dea3323a3b0a4844daa8f22c719b7e4f5a6c83cff613f94f18209512)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usdp-base-27ee)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
