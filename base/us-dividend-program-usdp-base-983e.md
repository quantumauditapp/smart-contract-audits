---
token: US Dividend Program (USDP)
ticker: USDP
network: base
risk_score: 60
status: medium
date: 2026-10-25
---

# US Dividend Program (USDP) (USDP) — Smart Contract Security Analysis | Base

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/us-dividend-program-usdp-base-983e)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation rates and pool access. While the code follows standard OpenZeppelin patterns, the high degree of administrative control poses a significant centralization risk to token holders.

> **Final Recommendation:** To improve security, consider transitioning ownership to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with a single point of failure. Implementing a timelock on sensitive functions like updateMintRate would provide transparency and allow the community to react to administrative changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes robust OpenZeppelin libraries for ERC-20 and governance features. 7.1 Architecture is sound, and 7.2 Code Security is high due to the use of standard, battle-tested… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner has the authority to mint tokens and halt transfers, which directly impacts 7.6 External interactions. While inflation is… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. This ensures immutability of the logic, which is a strength for security. No upgrade-related risks are present. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply at their discretion, which dilutes the value of existing holdings.

**Recommendation:** Restrict minting capabilities to a pre-defined schedule or move the authority to a decentralized governance mechanism to prevent arbitrary supply increases.


### `CP-05` — Centralized Transfer Control  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to toggle a switch that determines whether token transfers are allowed. This gives the owner the power to freeze user funds or halt trading activity.

**Recommendation:** Remove the ability for the owner to pause transfers, or implement a multi-sig requirement and a timelock to ensure that such drastic actions are only taken in emergencies.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xe2b6…9484 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 10,013 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

10,013 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $157K (DexScreener, all pools). 24h trading volume $2.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $2.32 — it does not hold a peg. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $157K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf427...36de`](https://basescan.org/address/0xf4276e7ed07a15394981706d4f7e7688e5d336de) |
| **Network** | Base |
| **Price** | $2.3200 |
| **24h Volume** | $2.14M |
| **Liquidity** | $156.7K |
| **Volume / Liquidity** | 13.7× |
| **Token Age** | 6h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3274 buys / 2869 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x15de101a15fccaec97d8ea3c357dcba87eac6d37ac52c608891c3bd54b03d188)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/us-dividend-program-usdp-base-983e)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
