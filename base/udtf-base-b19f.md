---
token: UDTF
ticker: UDTF
network: base
risk_score: 59
status: medium
date: 2026-10-28
---

# UDTF (UDTF) — Smart Contract Security Analysis | Base

> **Risk Score: 59/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/udtf-base-b19f)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The architecture relies heavily on a centralized owner account, which possesses significant control over token supply and transferability. While the code follows standard OpenZeppelin patterns, the centralization of power presents a notable risk to token holders.

> **Final Recommendation:** It is recommended to transition ownership to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with a single point of failure. Additionally, implementing a timelock on sensitive functions like updateMintRate would provide transparency and protection for token holders against sudden economic changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-tested OpenZeppelin libraries for ERC-20 and governance features. 7.1 Architecture and 7.2 Code Security are robust, adhering to standard implementation patterns. However… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are dominated by the owner's ability to mint tokens and restrict transfers. While 7.6 External interactions are minimal, the owner's capacity to modify the… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable, which provides security against proxy-related vulnerabilities but prevents logic updates without a migration.… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to increase the total supply of the token through the updateMintRate and release functions. This allows the owner to dilute the holdings of all existing token holders at their discretion.

**Recommendation:** Implement a timelock for minting operations or transition ownership to a decentralized governance model to ensure community oversight.


### `CP-05` — Centralized Transfer Control  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to enable or disable token transfers. This gives the owner the power to freeze user funds or halt market activity entirely.

**Recommendation:** Remove the ability to arbitrarily lock transfers or restrict this functionality to emergency scenarios governed by a multi-signature or decentralized vote.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 16 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

16 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $3.8M (DexScreener, all pools). 24h trading volume $1.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $3.8M of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdb39...d038`](https://basescan.org/address/0xdb3936ac73af40842fc818d891f73d6f4dd6d038) |
| **Network** | Base |
| **Price** | $0.7562 |
| **24h Volume** | $1.03M |
| **Liquidity** | $3.78M |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 7h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2177 buys / 2160 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x7de9069a43324be6cd450d30beb363920992d9cacaabee54dc52dbcb3a6fd423)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/udtf-base-b19f)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
