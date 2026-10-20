---
token: USOE
ticker: USOE
network: base
risk_score: 66
status: high
date: 2026-10-20
---

# USOE (USOE) — Smart Contract Security Analysis | Base

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usoe-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with governance (Votes) and vesting capabilities. The protocol relies on a centralized owner to manage inflation and liquidity pool restrictions. While the code follows standard OpenZeppelin patterns, the high level of administrative control over token supply and transferability presents a significant centralization risk.

> **Final Recommendation:** To improve security, consider transitioning the ownership to a multi-signature wallet or a decentralized governance contract (DAO) to mitigate the risks associated with a single point of failure. Implementing a timelock on sensitive functions like updateMintRate and lockPool would provide transparency and allow the community to react to administrative changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture utilizes robust OpenZeppelin standards for ERC-20, voting, and permit functionality. 7.1 Architecture and 7.2 Code Security are well-implemented, leveraging battle-tested libraries.… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner can unilaterally mint tokens up to a 2% annual cap and toggle transfer restrictions, which directly impacts 7.6 External… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable, which provides security against upgrade-related vulnerabilities but prevents logic patches without a migration. |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Token Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to increase the total supply of the token. This allows the owner to dilute existing holders' value at their discretion, provided they stay within the 2% annual cap.

**Recommendation:** Implement a timelock for minting operations or transition ownership to a DAO to ensure that supply changes are subject to community consensus.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to enable or disable token transfers. This gives the owner the ability to effectively freeze the token or prevent users from trading in specific liquidity pools.

**Recommendation:** Remove the ability to arbitrarily lock transfers, or restrict this functionality to a decentralized emergency response committee rather than a single owner address.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.3% in wallets, 80.0% in other contracts. 2,013 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,013 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $31K (DexScreener, all pools). 24h trading volume $176K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $31K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x61f0...c4b1`](https://basescan.org/address/0x61f0d41f369740978ade472f875d479a09efc4b1) |
| **Network** | Base |
| **Price** | $0. |
| **24h Volume** | $176.2K |
| **Liquidity** | $30.6K |
| **Volume / Liquidity** | 5.8× |
| **Token Age** | 13h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1213 buys / 1205 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xc09d82a7b75b5dacf5d4c12ffb8f48fee738ce46670e3382f9b4990b40ad1945)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usoe-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
