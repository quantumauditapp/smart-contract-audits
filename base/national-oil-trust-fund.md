---
token: National Oil Trust Fund
ticker: NOTF
network: base
risk_score: 59
status: medium
date: 2026-10-24
---

# National Oil Trust Fund (NOTF) — Smart Contract Security Analysis | Base

> **Risk Score: 59/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/national-oil-trust-fund-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with added governance, voting, and vesting capabilities. The protocol relies on a centralized owner to manage inflation rates and pool transfer restrictions. While the code follows standard OpenZeppelin patterns, the high degree of administrative control over token supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** To improve security, the protocol should transition ownership to a multi-signature wallet or a decentralized governance contract to prevent single-point-of-failure risks. Implementing a time-lock on sensitive functions like updateMintRate would provide the community with notice before significant economic changes occur.

Users should monitor the owner's activity, as the current configuration grants the owner total control over the token's economic parameters and transferability. Consider verifying the owner's identity and the governance process to ensure alignment with community interests.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, voting, and permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance risks are elevated due to the owner's ability to unilaterally alter the token supply and restrict market liquidity. The owner can trigger inflation via updateMintRate… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, which mitigates 7.7 Upgrades risks. The logic is immutable, ensuring that the current rules cannot be changed via proxy updates. This provides transparency for users… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to call updateMintRate and release, which can increase the total supply of tokens. This allows the owner to dilute the holdings of all existing token holders at their discretion.

**Recommendation:** Implement a time-lock for minting operations or transition control to a decentralized governance mechanism to ensure transparency and community oversight.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to enable or disable token transfers. This gives the owner the power to effectively freeze the market or prevent users from moving their assets.

**Recommendation:** Remove the ability to arbitrarily lock transfers or restrict this functionality to a decentralized emergency pause mechanism with clear, predefined conditions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 4,788 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,788 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $78K (DexScreener, all pools). 24h trading volume $329K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $78K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf09f...3469`](https://basescan.org/address/0xf09f87561b1b70bbb4fe326f48edb86737ec3469) |
| **Network** | Base |
| **Price** | $0.1251 |
| **24h Volume** | $328.7K |
| **Liquidity** | $78.4K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 12h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1509 buys / 1484 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x9377d0f30e482ccd2a7a0bdd40b61b2258bceb191e2bc6da8ee9455f91a395e7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/national-oil-trust-fund-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
