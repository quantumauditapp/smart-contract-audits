---
token: Facebook
ticker: FACEBOOK
network: bsc
risk_score: 81
status: high
date: 2026-10-28
---

# Facebook (FACEBOOK) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 81/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/facebook-bsc)

---

## Audit Summary

The contract is a standard ERC-20 token with custom fee logic. Ownership has been renounced, meaning privileged functions are now dormant. However, critical vulnerabilities exist in the internal swap and liquidity logic that could lead to unauthorized token movement and loss of funds.

> **Final Recommendation:** The contract should be considered high-risk due to the identified critical and high-severity vulnerabilities. Since ownership is renounced, the current code cannot be patched or updated to fix these issues.

Users should exercise extreme caution. If the token is intended for production use, a redeployment with a corrected codebase that properly handles return values and prevents unauthorized token transfers is strongly advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns with added fee-on-transfer logic. 7.1 Architecture is standard, but 7.2 Code Security is compromised by improper handling of external calls. 7.3… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance are currently static as ownership is renounced. No further changes to fee structures or tokenomics can be made by the deployer. The economic model relies on the… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. The code is immutable, which provides security against malicious updates but prevents patching the identified vulnerabilities. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 93.9% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 6.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function allows the contract to move tokens from any address that has approved the contract, potentially leading to unauthorized drainage of user funds.

**Recommendation:** Restrict the scope of token transfers to only those authorized by the contract's own internal logic or specific user-initiated actions.


### `CD-04` — Ignored Transfer Return Values  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function fails to check the return value of ERC-20 transfers, which may fail silently and lead to inconsistent state tracking.

**Recommendation:** Always check the boolean return value of ERC-20 transfer and transferFrom calls, or use OpenZeppelin's SafeERC20 library.


### `CD-03` — Locked ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract accepts ETH via receive functions but lacks any mechanism to withdraw or utilize these funds, effectively locking them permanently.

**Recommendation:** Implement a withdrawal function restricted to a secure address or ensure the contract does not accept ETH if it is not intended for use.


### `CD-02` — Precision Loss in Calculations  *(Severity: Low · Status: Unresolved)*

The functions _executeSwapAndLiquify and _transfer perform division before multiplication, which can lead to rounding errors and slight inaccuracies in fee calculations.

**Recommendation:** Reorder arithmetic operations to perform multiplication before division to maintain higher precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 25.6% of supply. Of that, 22.7% burned, 2.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.5% in wallets, 0.0% in other contracts. 61,410 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

61,410 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

93.9% of the pool's LP is burned or time-locked. 93.9% is locked in PinkLock02 until 26 Nov 2026 (28 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 6.1% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $390K (DexScreener, all pools). 24h trading volume $87.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4.5% on buy, 4.62% on sell. Market: $390K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3e64...6329`](https://bscscan.com/address/0x3e641bd686f6920144668c9f792ce2604d8d6329) |
| **Network** | BNB Chain |
| **Price** | $0.000836 |
| **24h Volume** | $87.16M |
| **Liquidity** | $390.5K |
| **Volume / Liquidity** | 223.2× |
| **Token Age** | 13h |
| **Top-10 Holders** | 25.6% of supply |
| **Buy / Sell Tax** | 4.5% / 4.6% |
| **24h Transactions** | 26671 buys / 5464 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xe7c20f494671a44ba50957661cc821ef9187b224)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/facebook-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
