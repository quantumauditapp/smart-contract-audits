---
token: iPhone Duo
ticker: IPHONE DUO
network: bsc
risk_score: 81
status: high
date: 2026-10-25
---

# iPhone Duo (IPHONE DUO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 81/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/iphone-duo-bsc)

---

## Audit Summary

The contract is a standard ERC-20 token with custom fee exclusion logic. Ownership has been renounced, meaning the privileged functions are now dormant and cannot be modified. However, the contract contains critical logic flaws in its internal swap and liquidity management, specifically regarding token transfers and fund handling.

> **Final Recommendation:** The contract is currently in a state where critical vulnerabilities cannot be patched due to renounced ownership. Users should be aware that the contract contains trapped ETH and unsafe transfer logic that may lead to unexpected token behavior during liquidity operations.

Future deployments should implement robust return value checking for all ERC-20 interactions and include a mechanism for the withdrawal of accidentally sent native assets to prevent permanent loss of funds.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns with 7.1 Architecture and 7.2 Code Security implemented. 7.3 Access Control is currently locked due to renounced ownership. 7.6 External interactions… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance are currently static. Since ownership is renounced, no further changes to fee exclusions or economic parameters can be made. The token economy is fixed as defined at… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported. The contract is immutable, which prevents malicious proxy updates but also prevents patching the identified critical vulnerabilities. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 96.1% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 3.9% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function uses transferFrom to move tokens from arbitrary addresses, potentially allowing unauthorized depletion of user balances if the allowance is set.

**Recommendation:** Restrict the source address in transferFrom to the contract's own balance or ensure strict validation of the caller.


### `CD-04` — Ignored Transfer Results  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function performs token transfers without checking the boolean return value, which may lead to silent failures in liquidity operations.

**Recommendation:** Always check the return value of ERC-20 transfer calls and revert if the transfer fails.


### `CD-03` — Trapped Native Assets  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function that accepts ETH, but there are no functions implemented to withdraw or utilize these funds, causing them to be permanently locked.

**Recommendation:** Implement an owner-restricted function to withdraw native assets from the contract.


### `CD-02` — Rounding Precision Loss  *(Severity: Low · Status: Unresolved)*

Calculations in _executeSwapAndLiquify and _transfer perform division before multiplication, which can lead to precision loss and incorrect fee calculations.

**Recommendation:** Perform all multiplications before divisions to maintain maximum precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 3.2% of supply. Of that, 1.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 2.2% in wallets, 0.0% in other contracts. 11,743 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

11,743 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

96.1% of the pool's LP is burned or time-locked. 96.1% is locked in PinkLock02 until 11 Nov 2026 (16 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 3.9% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $896K (DexScreener, all pools). 24h trading volume $24.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4% on buy, 4.28% on sell. Market: $896K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb0cc...0650`](https://bscscan.com/address/0xb0cc643eaffd28d4ed43d2793bcca54438380650) |
| **Network** | BNB Chain |
| **Price** | $17.2000 |
| **24h Volume** | $24.78M |
| **Liquidity** | $895.7K |
| **Volume / Liquidity** | 27.7× |
| **Token Age** | 21h |
| **Top-10 Holders** | 3.2% of supply |
| **Buy / Sell Tax** | 4.0% / 4.3% |
| **24h Transactions** | 5587 buys / 902 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x12bbfbeaf1aa78f58e8d82ddf910f3a92615acf1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/iphone-duo-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
