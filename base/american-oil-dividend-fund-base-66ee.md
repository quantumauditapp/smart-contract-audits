---
token: American Oil Dividend Fund
ticker: AODF
network: base
risk_score: 58
status: medium
date: 2026-10-21
---

# American Oil Dividend Fund (AODF) — Smart Contract Security Analysis | Base

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-base-66ee)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol exhibits centralized control, allowing the owner to mint tokens and restrict transferability. While the code follows standard OpenZeppelin patterns, the high degree of administrative privilege poses a significant trust requirement for token holders.

> **Final Recommendation:** To improve security, it is recommended to transition ownership to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single point of failure. Additionally, implementing a timelock on sensitive functions like updateMintRate would provide transparency and allow the community to react to administrative changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular and 7.2 Code Security is high due to standard implementation. 7.3… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner has the ability to mint tokens and toggle transferability, which directly impacts 7.8 Operations. While minting is capped at… |
| **Upgrades** | 3/10 | High | The contract is not upgradeable (7.7 Upgrades), which provides immutability for the core logic. This eliminates risks associated with proxy pattern vulnerabilities or malicious logic updates. The… |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Centralized Token Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to increase the total supply of tokens via the updateMintRate and release functions. This allows for potential supply inflation that dilutes the value of existing holdings.

**Recommendation:** Consider implementing a hard cap on the total supply or moving the minting authority to a decentralized governance mechanism.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to enable or disable token transfers globally. This grants the owner the ability to freeze user funds or prevent trading at their discretion.

**Recommendation:** Remove the ability to pause transfers or implement a community-driven voting process for any transfer restrictions.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $52K (DexScreener, all pools). 24h trading volume $273K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $52K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8f74...de36`](https://basescan.org/address/0x8f7460308301a69a0ccc0997b07358427080de36) |
| **Network** | Base |
| **Price** | $0.00000056 |
| **24h Volume** | $272.9K |
| **Liquidity** | $51.7K |
| **Volume / Liquidity** | 5.3× |
| **Token Age** | 19h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1812 buys / 1774 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x57901be0c0e183a8620ebec1d29d8d8451c4d9d5441e76e64eb3d142b04b9531)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-base-66ee)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
