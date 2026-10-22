---
token: XTO
ticker: XTO
network: base
risk_score: 76
status: high
date: 2026-10-22
---

# XTO (XTO) — Smart Contract Security Analysis | Base

> **Risk Score: 76/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xto-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with governance capabilities and custom minting/vesting logic. The contract relies on a centralized owner to manage inflation rates and pool access, which introduces significant trust requirements for token holders. Coverage items: 7.1 Architecture (Standard), 7.2 Code Security (Good), 7.3 Access Control (Centralized), 7.4 Economic (Inflationary), 7.5 Governance (Owner-controlled), 7.6 External (None), 7.7 Upgrades (N/A), 7.8 Operations (Standard).

> **Final Recommendation:** It is recommended to transition the ownership of the contract to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with a single point of failure. Additionally, implementing a timelock for sensitive functions like updateMintRate would provide transparency and allow the community to react to significant changes in tokenomics.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The codebase utilizes standard OpenZeppelin libraries for ERC-20 and governance, ensuring robust implementation of core token standards. The logic is clean and follows modern Solidity patterns.… |
| **Governance / Economics** | 3/10 | High | The protocol exhibits high centralization, as the owner holds absolute authority over token supply and transferability. The owner can unilaterally mint tokens up to a 2% annual cap and toggle the… |
| **Upgrades** | 4/10 | Medium | The contract is not a proxy and does not support upgrades, which eliminates risks associated with implementation changes. This ensures that the logic remains as audited and cannot be altered by the… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to call updateMintRate and release, which allows them to mint new tokens and increase the total supply. This action dilutes the value of existing holdings and can be performed at the owner's discretion within the defined limits.

**Recommendation:** Implement a timelock mechanism for all supply-altering functions to ensure that token holders are notified before any significant changes to the total supply occur.


### `CP-05` — Owner Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to enable or disable token transfers. This gives the owner the power to freeze user funds or restrict trading activity at any time.

**Recommendation:** Restrict the use of transfer-blocking functions to emergency scenarios only, or replace the owner-only control with a decentralized voting mechanism to prevent potential abuse.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 4,956 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,956 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $211K (DexScreener, all pools). 24h trading volume $403K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $211K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7164...06fc`](https://basescan.org/address/0x71640ab42abfb1c13d5e6a8e99b2cee1c90906fc) |
| **Network** | Base |
| **Price** | $0.4008 |
| **24h Volume** | $402.9K |
| **Liquidity** | $211.1K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 15h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1588 buys / 1492 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xc26cd34a8561eab42dec324c17027013f22cb181b393df601a06d9180dbe108b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xto-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
