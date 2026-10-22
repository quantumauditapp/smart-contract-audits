---
token: United Dividend Trust Fund
ticker: UDTF
network: base
risk_score: 78
status: high
date: 2026-10-22
---

# United Dividend Trust Fund (UDTF) — Smart Contract Security Analysis | Base

> **Risk Score: 78/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-dividend-trust-fund-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation rates and pool access. While the code follows standard OpenZeppelin patterns, the high degree of administrative control over supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** Token holders should be aware that the owner has the capability to mint new tokens and restrict transfers. It is recommended to transition ownership to a decentralized multi-signature wallet or a DAO governance contract to mitigate the risk of a single point of failure. 

Ensure that all administrative actions are communicated transparently to the community. Consider implementing a timelock on sensitive functions like updateMintRate to provide users with advance notice of supply changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The architecture leverages well-audited OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture and 7.2 Code Security are robust, utilizing standard inheritance patterns.… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are centralized. The owner has the ability to mint tokens and halt transfers, which directly impacts 7.4 Economic stability. These mechanisms are transparent… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable, which provides security against unauthorized logic changes but prevents patching if a bug is discovered. |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to increase the total supply of tokens. This allows the owner to dilute the holdings of all existing token holders at their discretion.

**Recommendation:** Implement a timelock on minting functions or transition ownership to a DAO to ensure community oversight of supply changes.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to toggle the ability for tokens to be transferred. This gives the owner the power to freeze user assets or halt market activity.

**Recommendation:** Remove the ability to pause transfers or implement a multi-signature requirement for such drastic actions to prevent unilateral control.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.1% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,211 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,211 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $50K (DexScreener, all pools). 24h trading volume $120K (DexScreener, all pools).

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
| **Contract** | [`0x5e35...ea30`](https://basescan.org/address/0x5e35d4c7d4a8f95f3a68b20f1b08cacc6c74ea30) |
| **Network** | Base |
| **Price** | $0.004949 |
| **24h Volume** | $120.4K |
| **Liquidity** | $49.8K |
| **Volume / Liquidity** | 2.4× |
| **Token Age** | 21h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2728 buys / 2568 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xb093f02a08c1209332f90a144be830c2a96b09ec93e3b867b1fad0124555f0c6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-dividend-trust-fund-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
