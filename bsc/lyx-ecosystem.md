---
token: LYX Ecosystem
ticker: LYX
network: bsc
risk_score: 84
status: high
date: 2026-10-30
---

# LYX Ecosystem (LYX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lyx-ecosystem-bsc)

---

## Audit Summary

The contract is a standard ERC-20 token with custom fee exclusion logic. Ownership has been renounced, meaning privileged functions are now dormant. However, the contract contains critical vulnerabilities in its internal swap and liquidity management logic that could lead to unauthorized token movement and loss of funds.

> **Final Recommendation:** The contract should be considered high-risk due to the identified critical and high-severity vulnerabilities. Since ownership is renounced, these issues cannot be patched via contract updates.

It is strongly recommended to migrate to a new, audited contract implementation that properly handles ERC-20 return values and implements secure arithmetic practices. Users should exercise extreme caution when interacting with the current contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns but includes flawed internal swap logic. 7.1 Architecture is standard, but 7.2 Code Security is compromised by improper handling of transfer return… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance are currently static as ownership is renounced. 7.8 Operations are limited to standard token transfers. No active governance mechanisms exist to modify the contract… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. The code is immutable, which provides security against malicious upgrades but prevents fixing the identified vulnerabilities. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 95.5% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 4.4% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function allows the contract to move tokens from any address that has granted an allowance, potentially leading to unauthorized drainage of user funds.

**Recommendation:** Restrict the scope of transferFrom to only authorized contract-controlled addresses or remove the ability to pull tokens from arbitrary user addresses.


### `CD-04` — Ignored Transfer Return Values  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function fails to check the boolean return value of ERC-20 transfers, which can lead to silent failures where tokens are not actually moved.

**Recommendation:** Always check the return value of transfer and transferFrom calls, or use OpenZeppelin's SafeERC20 library.


### `CD-03` — Locked ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function that accepts ETH, but there is no mechanism to withdraw or transfer these funds out, causing them to be permanently locked.

**Recommendation:** Implement a withdrawal function restricted to a secure address or remove the receive function if ETH handling is not required.


### `CD-02` — Rounding Errors due to Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

Calculations in _executeSwapAndLiquify and _transfer perform division before multiplication, which leads to precision loss and incorrect fee calculations.

**Recommendation:** Rearrange mathematical operations to perform multiplication before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 24.3% of supply. Of that, 23.3% burned, 0.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.6% in wallets, 0.0% in other contracts. 31,469 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

31,469 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

95.5% of the pool's LP is burned or time-locked. 95.5% is locked in PinkLock02 until 28 Nov 2026 (28 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 4.5% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.2M (DexScreener, all pools). 24h trading volume $61.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4.5% on buy, 4.66% on sell. Market: $1.2M of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe07d...ad1e`](https://bscscan.com/address/0xe07d4bd6b94cec4e412c8f9735bc8fc97d25ad1e) |
| **Network** | BNB Chain |
| **Price** | $14.4500 |
| **24h Volume** | $61.37M |
| **Liquidity** | $1.16M |
| **Volume / Liquidity** | 53.0× |
| **Token Age** | 7h |
| **Top-10 Holders** | 24.3% of supply |
| **Buy / Sell Tax** | 4.5% / 4.7% |
| **24h Transactions** | 17009 buys / 2795 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x53ca21812cbc904bb13d9773efe488717db6fda8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lyx-ecosystem-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
