---
token: 第一个回购销毁模式
ticker: GANGBALL
network: bsc
risk_score: 65
status: high
date: 2026-10-29
---

# 第一个回购销毁模式 (GANGBALL) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gangball-bsc)

---

## Audit Summary

GangToken is a standard ERC-20 token with additional administrative functions allowing a 'launchpad' address to manage liquidity pairs and perform token transfers on behalf of users. The architecture relies on centralized control for critical operations, which introduces significant trust requirements. 7.1 Architecture: Centralized. 7.2 Code Security: Standard. 7.3 Access Control: Restricted. 7.4 Economic: High risk due to minting/pulling capabilities. 7.5 Governance: Centralized. 7.6 External: Standard. 7.7 Upgrades: N/A. 7.8 Operations: High dependency on launchpad.

> **Final Recommendation:** We recommend transitioning the 'launchpad' role to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single compromised key. Additionally, consider implementing a timelock for sensitive administrative functions like setPair to provide users with notice before changes to the token's economic rules take effect.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements standard ERC-20 functionality with clean logic for transfers and allowances. The use of OpenZeppelin-style patterns ensures compatibility with standard wallets and DEXs.… |
| **Governance / Economics** | 1/10 | High | The economic model is heavily centralized, granting the launchpad address the ability to move user funds and modify pair settings. This creates a trust-based environment where holders are vulnerable… |
| **Upgrades** | 2/10 | High | The contract is not upgradeable and does not utilize proxy patterns. Logic is immutable once deployed, providing certainty to users regarding the contract's behavior. No upgrade-related risks are… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Balances  *(Severity: Medium · Status: Unresolved)*

The 'launchpad' address has the authority to call reclaim and pullFor functions, which can move tokens from user wallets to the launchpad address. This centralized control allows the administrator to unilaterally affect user balances and potentially drain liquidity.

**Recommendation:** Restrict the scope of the launchpad's authority or implement a decentralized governance mechanism to oversee these privileged actions. Ensure that the launchpad address is secured by a multi-signature wallet.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x0eb6…5e43 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 50.1% of supply. Of that, 8.2% burned — not holders that can sell, so excluded from the concentration score. What remains: 6.9% in wallets, 35.0% in other contracts. The deployer/owner wallet itself holds 1.0%. 514 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

514 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $515K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb1f2...99a3`](https://bscscan.com/address/0xb1f21c4509aebd494ee58c80da3e07d979d499a3) |
| **Network** | BNB Chain |
| **Price** | $0.00001956 |
| **24h Volume** | $515.3K |
| **Liquidity** | $11.9K |
| **Volume / Liquidity** | 43.2× |
| **Token Age** | 7h |
| **Top-10 Holders** | 50.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4509 buys / 6902 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x4b90909a4d935d0f969589eb052395e62a9d4a8f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gangball-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
