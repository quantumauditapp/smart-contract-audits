---
token: US Dividend Reserve (USDR)
ticker: USDR
network: base
risk_score: 67
status: high
date: 2026-10-20
---

# US Dividend Reserve (USDR) (USDR) — Smart Contract Security Analysis | Base

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/us-dividend-reserve-usdr-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage minting rates and pool access. While the code follows standard OpenZeppelin implementations, the high level of administrative control over token supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** To improve security, consider transitioning the ownership to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single compromised key. Additionally, implementing a timelock on sensitive functions like updateMintRate would provide transparency and allow the community to react to significant changes in token supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture utilizes standard OpenZeppelin libraries for ERC-20, Votes, and Permit functionality, ensuring robust base logic. 7.1 Architecture and 7.2 Code Security are well-implemented… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily skewed toward the owner. The ability to mint tokens via updateMintRate and release functions allows for potential supply inflation. 7.6 External… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable, which provides security against hidden logic changes but prevents emergency patching. Future changes would… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to mint new tokens, which directly dilutes the value of existing holdings. This grants the owner unilateral control over the total supply of the token.

**Recommendation:** Implement a timelock for minting operations or transition ownership to a DAO to ensure community oversight of supply changes.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to enable or disable transfers for specific pools. This allows the owner to freeze user funds or restrict trading at their discretion.

**Recommendation:** Remove the ability to arbitrarily lock pools or implement a transparent, policy-based mechanism that limits the owner's ability to freeze assets.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.0% in wallets, 80.2% in other contracts. The deployer/owner wallet itself holds 16.0%. 2,541 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,541 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $49K (DexScreener, all pools). 24h trading volume $66K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.002405 — it does not hold a peg. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $49K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1438...e1a1`](https://basescan.org/address/0x1438a02715d50decb15c00eac9f57bd325f8e1a1) |
| **Network** | Base |
| **Price** | $0.002405 |
| **24h Volume** | $66.5K |
| **Liquidity** | $49.1K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 13h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1825 buys / 1813 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x8d8406e1f6dc8f832b9698d8483b40d9f5997377c34f905f7c3e7122a5595d17)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/us-dividend-reserve-usdr-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
