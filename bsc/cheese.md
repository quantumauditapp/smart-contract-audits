---
token: Cheese
ticker: CHEESE
network: bsc
risk_score: 69
status: high
date: 2026-11-02
---

# Cheese (CHEESE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 69/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cheese-bsc)

---

## Audit Summary

CheeseToken is an ERC-20 token with centralized administrative controls. The system relies on a 'system' address that holds significant power over token supply, user balances, and transfer fees. While the code follows standard ERC-20 patterns, the centralization of power presents a high risk to token holders.

> **Final Recommendation:** The protocol should transition to a multi-signature wallet or a decentralized governance contract to manage the 'system' role. Implementing a time-lock on administrative functions would provide users with visibility into upcoming changes to fees or supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements standard ERC-20 functionality with robust library usage. 7.1 Architecture is straightforward, utilizing a single-contract design. 7.2 Code Security is generally high, though… |
| **Governance / Economics** | 1/10 | High | 7.5 Governance is entirely centralized under the 'system' address, which lacks transparency or time-locks. 7.4 Economic risks are significant as the system can arbitrarily mint tokens or burn user… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable, which provides security against hidden logic changes but prevents emergency patching. 7.8 Operations are limited… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CP-02` — Arbitrary Balance Manipulation  *(Severity: High · Status: Unresolved)*

The 'system' address can call burnBySystem to remove tokens from any user's balance, effectively allowing the controller to seize or destroy user funds.

**Recommendation:** Remove the ability for the system to burn tokens from arbitrary addresses; restrict burning to the caller's own balance.


### `CP-01` — Centralized Supply Control  *(Severity: Medium · Status: Unresolved)*

The 'system' address can mint new tokens at will using mintEarnable and mintPoolSeed, which dilutes the value of existing holdings.

**Recommendation:** Implement a hard cap on total supply or move minting authority to a decentralized governance process.


### `CP-07` — Centralized Fee Management  *(Severity: Medium · Status: Unresolved)*

The 'system' address can influence transfer fees and tax collection, allowing for dynamic changes to the economic cost of trading.

**Recommendation:** Define fee parameters in the contract as constants or use a governance-controlled parameter with a maximum cap.


### `CD-01` — Rounding Loss in Calculations  *(Severity: Low · Status: Unresolved)*

The contract performs division before multiplication in the _update function, which can lead to precision loss during fee calculations.

**Recommendation:** Always multiply before dividing to maintain precision, or use a library like ABDKMath64x64 for fixed-point arithmetic.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 84.0% of supply. Of that, 54.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.8% in wallets, 14.0% in other contracts. 335 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

335 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $271K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: system — a contract. Code: not upgradeable (no proxy). Fees: 2% on buy, 3% on sell. Market: $13K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8caf...6e94`](https://bscscan.com/address/0x8cafc39863386538b04172b268bdd38e9f626e94) |
| **Network** | BNB Chain |
| **Price** | $0.002448 |
| **24h Volume** | $271.2K |
| **Liquidity** | $12.6K |
| **Volume / Liquidity** | 21.5× |
| **Token Age** | 6h |
| **Top-10 Holders** | 84.0% of supply |
| **Buy / Sell Tax** | 2.0% / 3.0% |
| **24h Transactions** | 2147 buys / 2996 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xed840d645290c00b07b04e8aa8b73db5ebdb5282)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cheese-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
