---
token: CRAZYCOIN
ticker: CRAZYCOIN
network: bsc
risk_score: 47
status: medium
date: 2026-10-22
---

# CRAZYCOIN (CRAZYCOIN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 47/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/crazycoin-bsc)

---

## Audit Summary

The TapeoutOpenFourToken is an EIP-1167 minimal clone implementation. The contract exhibits high centralization risk due to privileged roles having extensive control over transfer logic, fee structures, and external dependency routing. While the core ERC-20 functionality is standard, the complex tax and migration logic introduces significant trust requirements for users.

> **Final Recommendation:** Users should exercise caution due to the high degree of centralization. The protocol should consider implementing a multi-signature wallet or a time-lock mechanism for the privileged modules to mitigate the risk of sudden, malicious changes to transfer logic or fee structures.

Developers should perform a comprehensive audit of the external modules (tokenModule, taxVault, migrateModule) as these contracts effectively govern the token's behavior and economic security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes a modular approach for tax and migration handling. 7.1 Architecture: EIP-1167 clone pattern ensures immutable logic. 7.2 Code Security: Standard ERC-20 implementation is… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic: The token relies on dynamic fee structures and external liquidity pools. 7.5 Governance: No decentralized governance exists; all parameters are controlled by privileged modules. 7.6… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The contract is an immutable EIP-1167 clone, meaning the logic cannot be upgraded. 7.8 Operations: Operational risk is high due to the ability of privileged modules to modify critical… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `CP-03` — Centralized Control Over Critical Dependencies  *(Severity: High · Status: Unresolved)*

The postInitialize function allows a privileged 'tokenModule' to change the addresses of critical external contracts that the token relies on for every transfer. This grants the controller the ability to redirect token logic or intercept funds.

**Recommendation:** Restrict the ability to change these addresses to a multi-signature wallet or implement a time-lock to ensure transparency and prevent immediate malicious redirection.


### `CP-07` — Dynamic Fee Manipulation  *(Severity: Medium · Status: Unresolved)*

Privileged modules can modify transfer fees via onMigrate, claimFee, and onBondingTrade. This allows the controller to change the economic cost of transactions at any time without user consent.

**Recommendation:** Implement a cap on the maximum fee that can be set and provide an on-chain event notification whenever fee parameters are updated.


### `CD-01` — Rounding Loss Due to Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

The _doDispatchFee function performs division before multiplication, which can lead to precision loss and minor discrepancies in fee calculations.

**Recommendation:** Rearrange the arithmetic operations to perform multiplication before division to maintain higher precision.


### `CP-05` — Privileged Control Over Transfer Functionality  *(Severity: Informational · Status: Unresolved)*

Privileged functions can toggle the 'swapping' state, which directly impacts whether transfers or sales are permitted. This creates a risk where a controller could arbitrarily halt trading for users. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Document the intended use of the 'swapping' switch and provide clear public communication when such states are toggled to maintain user trust.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 97.6% of supply. Of that, 1.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.5% in wallets, 95.1% in other contracts. 2,063 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,063 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $120K (DexScreener, all pools). 24h trading volume $374K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $120K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfeef...ffff`](https://bscscan.com/address/0xfeef9e068dcd8d9b662d6ad70e946cc4e31dffff) |
| **Network** | BNB Chain |
| **Price** | $0.003309 |
| **24h Volume** | $373.8K |
| **Liquidity** | $120.2K |
| **Volume / Liquidity** | 3.1× |
| **Token Age** | 12h |
| **Top-10 Holders** | 97.6% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 894 buys / 523 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xa24fda2a02cef2b24ea31ddd1a1d665e9fa55092)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/crazycoin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
