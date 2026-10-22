---
token: 4cat
ticker: 4CAT
network: bsc
risk_score: 57
status: medium
date: 2026-10-22
---

# 4cat (4CAT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/4cat-bsc-5779)

---

## Audit Summary

The protocol is a minimal clone (EIP-1167) of a token contract. Ownership has been renounced, effectively locking administrative functions that previously controlled transfer modes and fee parameters. The code is immutable and functions as a standard ERC-20 token with additional fee-handling logic.

> **Final Recommendation:** Since ownership is renounced, the contract is effectively immutable. Users should be aware that fee structures and transfer rules are locked in their current state. No further action is required for the current deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes EIP-1167 minimal clones to minimize deployment costs. Code security is generally robust, though minor arithmetic precision issues exist in fee calculations. 7.1… |
| **Governance / Economics** | 1/10 | High | Economic parameters are currently fixed due to the renounced ownership. 7.4 Economic: Fee logic is present but immutable. 7.5 Governance: No active governance exists as ownership is renounced. The… |
| **Upgrades** | 8/10 | Low | The contract is a minimal clone and is not upgradeable. 7.7 Upgrades: No upgrade mechanism exists. 7.8 Operations: Operational risks are minimal given the immutable nature of the contract. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `CD-02` — State Variable Shadowing  *(Severity: High · Status: Unresolved)*

The contract contains instances where local variables shadow state variables, potentially leading to incorrect logic execution in sensitive functions.

**Recommendation:** Rename local variables to avoid conflicts with state variables.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x0e34…5100 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CD-01` — Rounding Loss in Fee Calculations  *(Severity: Low · Status: Unresolved)*

The functions _dispatchFee and normalizeAmount perform division before multiplication, which can lead to precision loss in fee calculations.

**Recommendation:** Reorder operations to multiply before dividing to maintain precision.


### `CP-05` — Dormant Administrative Transfer Controls  *(Severity: Informational · Status: Unresolved)*

Functions like setMode, addLiquidity, and swapForToken allow changing transfer rules or liquidity states. Because ownership is renounced, these functions are now dormant and cannot be called by anyone.

**Recommendation:** No action required as the functions are effectively disabled.


### `CP-07` — Dormant Fee Parameter Controls  *(Severity: Informational · Status: Unresolved)*

Functions such as postMigrate, sendFee, and claimFee allow modification of fee settings. These are now inaccessible due to the renounced ownership.

**Recommendation:** No action required.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 41.1% of supply. What remains: 11.0% in wallets, 30.1% in other contracts. 840 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

840 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $1.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0d93...ffff`](https://bscscan.com/address/0x0d939f5a7daf347332fc21682a791c3d292bffff) |
| **Network** | BNB Chain |
| **Price** | $0.00003096 |
| **24h Volume** | $1.05M |
| **Liquidity** | $18.2K |
| **Volume / Liquidity** | 57.6× |
| **Token Age** | 4h |
| **Top-10 Holders** | 41.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8098 buys / 7866 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xaf19dba6f0aac1bd96b3f6f3910fb4ace87d5d94)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/4cat-bsc-5779)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
