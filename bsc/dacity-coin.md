---
token: Dacity Coin
ticker: DACITY
network: bsc
risk_score: 84
status: high
date: 2026-10-23
---

# Dacity Coin (DACITY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dacity-coin-bsc)

---

## Audit Summary

The contract is a standard ERC-20 token with custom fee logic. While ownership has been renounced, preventing further administrative changes, the contract contains critical flaws in its internal swap and liquidity mechanisms that pose a risk to user funds and operational integrity.

> **Final Recommendation:** The contract should be redeployed with corrected logic for the swap and liquidity functions. Specifically, the implementation must validate the return values of all ERC-20 transfers and ensure that ETH trapped in the contract can be recovered or utilized correctly.

Users should exercise extreme caution as the current implementation of the liquidity swap mechanism allows for unauthorized token movement and ignores transfer success status, which could lead to permanent loss of funds.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements standard ERC-20 functionality with custom fee exclusion logic. 7.1 Architecture is straightforward, but 7.2 Code Security is compromised by improper handling of external… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance risks are mitigated by the renounced ownership status. No further changes to fee structures or administrative parameters are possible. The economic model relies on the… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. The implementation is immutable, ensuring no future logic changes can be introduced by the original deployer. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 98.2% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 1.4% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function uses transferFrom to move tokens from arbitrary addresses, potentially allowing the contract to drain tokens from users who have approved the contract.

**Recommendation:** Restrict the source of tokens in transferFrom to only the contract's own balance or explicitly authorized addresses.


### `CD-04` — Ignored Transfer Results  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function performs token transfers without checking the boolean return value, which may lead to silent failures where the contract assumes a transfer succeeded when it did not.

**Recommendation:** Always check the return value of ERC-20 transfers or use OpenZeppelin's SafeERC20 library.


### `CD-03` — Trapped ETH  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function that accepts ETH, but lacks any mechanism to withdraw or transfer that ETH out of the contract, effectively locking it forever.

**Recommendation:** Implement an emergency withdrawal function to allow the recovery of accidentally sent ETH.


### `CD-02` — Rounding Errors in Math  *(Severity: Low · Status: Unresolved)*

The contract performs division before multiplication in _executeSwapAndLiquify and _transfer, which leads to precision loss and inaccurate fee calculations.

**Recommendation:** Perform all multiplication operations before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.5% of supply. Of that, 80.0% burned, 0.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 0.2% in other contracts. 13,372 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

13,372 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

98.2% of the pool's LP is burned or time-locked. 98.2% is locked in PinkLock02 until 13 Nov 2026 (20 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 1.8% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $371K (DexScreener, all pools). 24h trading volume $7.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3.9% on buy, 3.95% on sell. Market: $371K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3d89...4fd4`](https://bscscan.com/address/0x3d894163557875aeeac54685b442ab9e4b2d4fd4) |
| **Network** | BNB Chain |
| **Price** | $0.05183 |
| **24h Volume** | $7.29M |
| **Liquidity** | $371.1K |
| **Volume / Liquidity** | 19.7× |
| **Token Age** | 8h |
| **Top-10 Holders** | 80.5% of supply |
| **Buy / Sell Tax** | 3.9% / 4.0% |
| **24h Transactions** | 6313 buys / 1777 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xc76955b4e501c51fca0dc746b9b3203a2331b04a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dacity-coin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
