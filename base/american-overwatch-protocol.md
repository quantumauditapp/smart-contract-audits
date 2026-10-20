---
token: American Overwatch Protocol
ticker: AOP
network: base
risk_score: 67
status: high
date: 2026-10-20
---

# American Overwatch Protocol (AOP) — Smart Contract Security Analysis | Base

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The architecture relies on a centralized owner to manage inflation, pool locking, and vesting releases. While the code follows standard OpenZeppelin patterns, the high degree of administrative control poses a significant centralization risk to token holders.

> **Final Recommendation:** It is recommended to transition the ownership of the contract to a decentralized governance model, such as a DAO or a multi-signature wallet, to mitigate the risks associated with a single point of failure. Implementing a timelock on sensitive functions like updateMintRate and lockPool would provide transparency and allow the community to react to administrative changes.

Furthermore, consider documenting the specific conditions under which the pool is intended to be locked to ensure transparency for liquidity providers. Regular audits of the administrative address's security posture are advised, as the owner holds total control over the token's economic parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, Votes, and Permitting. 7.1 Architecture is modular, and 7.2 Code Security is high due to standard implementation patterns. 7.3… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner has unilateral power to mint tokens and halt transfers, which directly impacts 7.6 External interactions with liquidity… |
| **Upgrades** | 3/10 | High | The contract is not upgradeable (7.7 Upgrades), which provides immutability for the logic. This eliminates risks associated with proxy storage collisions or malicious implementation swaps. The… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to increase the total supply of tokens. This allows the owner to dilute the holdings of all other token holders at their discretion.

**Recommendation:** Implement a timelock for all supply-altering functions or transition ownership to a decentralized governance contract.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to enable or disable token transfers. This gives the owner the power to freeze user funds or prevent trading on decentralized exchanges.

**Recommendation:** Remove the ability to arbitrarily lock transfers or restrict this functionality to a decentralized voting process.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.3% in wallets, 80.0% in other contracts. 1,788 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,788 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $39K (DexScreener, all pools). 24h trading volume $188K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $39K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3a00...e2c8`](https://basescan.org/address/0x3a00be1c3d201c9c6f4f8bd3f456aff6ee81e2c8) |
| **Network** | Base |
| **Price** | $0. |
| **24h Volume** | $187.8K |
| **Liquidity** | $39.3K |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 12h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1239 buys / 1131 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xf052c32775a2b607f43d5477b43e3fcc3d38184b1df6a9823f5d835bcccbb96f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
