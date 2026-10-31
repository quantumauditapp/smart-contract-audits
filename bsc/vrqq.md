---
token: VRQQ
ticker: VRQQ
network: bsc
risk_score: 82
status: high
date: 2026-10-31
---

# VRQQ (VRQQ) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 82/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vrqq-bsc)

---

## Audit Summary

The Token contract implements standard ERC-20 functionality with custom fee exclusion logic. Ownership has been renounced, meaning privileged functions are now dormant. However, critical flaws in the internal swap logic and ETH handling pose significant risks to token integrity and fund accessibility.

> **Final Recommendation:** The contract should be considered high-risk due to the critical vulnerability in the swap logic that allows unauthorized token movement. Since ownership is renounced, the current code cannot be patched or updated to fix these issues.

Users and liquidity providers should exercise extreme caution. The trapped ETH in the contract is permanently inaccessible, and the token transfer mechanism is unreliable due to the ignored return values in the swap function.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns but contains flawed internal logic in the swap mechanism. 7.1 Architecture is standard, but 7.2 Code Security is compromised by unchecked return… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance are currently static as ownership is renounced. No further changes to fee exclusions or economic parameters can be made by the deployer. The protocol relies entirely… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. The code is immutable, which provides security against malicious upgrades but prevents patching the identified critical vulnerabilities. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 96.0% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 2.4% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function uses transferFrom to move tokens from arbitrary addresses, potentially allowing the contract to drain tokens from any user who has approved the contract.

**Recommendation:** Restrict the source address in transferFrom to only the contract's own balance or authorized liquidity pools.


### `CD-04` — Unchecked ERC-20 Transfer Result  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function ignores the boolean return value of ERC-20 transfers, which can lead to silent failures where tokens are not moved as expected.

**Recommendation:** Always check the return value of transfer and transferFrom calls, or use OpenZeppelin's SafeERC20 library.


### `CD-03` — Trapped ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function that accepts ETH, but there is no mechanism to withdraw or transfer these funds out, causing them to be permanently locked.

**Recommendation:** Implement an owner-restricted withdrawal function to recover accidentally sent ETH.


### `CD-02` — Rounding Loss via Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

The _executeSwapAndLiquify and _transfer functions perform division before multiplication, which leads to precision loss and incorrect fee calculations.

**Recommendation:** Perform all multiplications before divisions to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 95.8% of supply. Of that, 95.2% burned, 0.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 0.0% in other contracts. 39,377 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

39,377 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

96.0% of the pool's LP is burned or time-locked. 96.0% is locked in PinkLock02 until 20 Nov 2026 (19 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 4.0% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $73K (DexScreener, all pools). 24h trading volume $13.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3.9% on buy, 3.91% on sell. Market: $73K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xea1e...09ec`](https://bscscan.com/address/0xea1ea4b73507840c1969d16f674742be976409ec) |
| **Network** | BNB Chain |
| **Price** | $0. |
| **24h Volume** | $13.07M |
| **Liquidity** | $73.0K |
| **Volume / Liquidity** | 179.1× |
| **Token Age** | 19h |
| **Top-10 Holders** | 95.8% of supply |
| **Buy / Sell Tax** | 3.9% / 3.9% |
| **24h Transactions** | 15639 buys / 4349 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x42c5d5786ae898438544da8e1d96f884b11a6fce)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vrqq-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
