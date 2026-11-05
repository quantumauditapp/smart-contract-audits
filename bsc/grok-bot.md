---
token: Grok Bot
ticker: GROK BOT
network: bsc
risk_score: 84
status: high
date: 2026-11-05
---

# Grok Bot (GROK BOT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grok-bot-bsc)

---

## Audit Summary

The contract implements a standard ERC-20 token with custom fee exclusion logic. While ownership has been renounced, preventing further administrative changes, the contract contains critical logic flaws in its internal swap and liquidity mechanisms that pose significant risks to user funds and contract integrity. Coverage includes 7.1 Architecture, 7.2 Code Security, 7.3 Access Control, 7.4 Economic, 7.5 Governance, 7.6 External, 7.7 Upgrades, 7.8 Operations.

> **Final Recommendation:** The contract should be considered unsafe for deployment due to the critical vulnerability allowing unauthorized token movement. It is recommended to redeploy a new version that strictly adheres to standard ERC-20 implementation patterns and removes the flawed internal swap logic.

If the contract is already live, users should be warned that the contract's internal liquidity mechanisms are non-functional and potentially exploitable. There is no path to remediation for the trapped ETH or the critical transfer logic flaws without a full migration to a new contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture relies on standard ERC-20 patterns but introduces dangerous logic in the _executeSwapAndLiquify function. It fails to validate return values from external token transfers, which can… |
| **Governance / Economics** | 6/10 | Medium | Ownership has been renounced, meaning no further changes can be made to the fee exclusion list or other administrative parameters. This effectively locks the current economic configuration. No… |
| **Upgrades** | 6/10 | Medium | The contract is not upgradeable and does not utilize proxy patterns. The logic is immutable, ensuring that the current vulnerabilities cannot be patched via administrative action. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 96.3% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 3.6% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function allows the contract to move tokens from any address that has previously approved the contract, potentially leading to unauthorized drainage of user funds.

**Recommendation:** Restrict the scope of token transfers to only those explicitly authorized by the user and ensure the contract does not initiate transfers on behalf of arbitrary users.


### `CD-04` — Ignored Transfer Return Values  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function ignores the boolean return value of ERC-20 transfers, which may fail silently without reverting the transaction.

**Recommendation:** Always check the return value of token transfers or use SafeERC20 to ensure the transfer was successful.


### `CD-03` — Trapped ETH  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function that accepts ETH, but there is no mechanism to withdraw or utilize these funds, effectively trapping them in the contract forever.

**Recommendation:** Implement a withdrawal function restricted to a designated address or remove the receive function if ETH handling is not required.


### `CD-02` — Precision Loss in Calculations  *(Severity: Low · Status: Unresolved)*

The contract performs division before multiplication in _executeSwapAndLiquify and _transfer, which leads to rounding errors and potential loss of precision in fee calculations.

**Recommendation:** Perform all multiplications before divisions to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.8% of supply. Of that, 90.0% burned, 0.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.4% in wallets, 0.0% in other contracts. 29,744 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

29,744 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

96.3% of the pool's LP is burned or time-locked. 96.3% is locked in PinkLock02 until 15 Nov 2026 (9 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 3.7% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $143K (DexScreener, all pools). 24h trading volume $9.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4% on buy, 4% on sell. Market: $143K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xed74...776e`](https://bscscan.com/address/0xed743a395ef1a41300969978db7cb59a1e77776e) |
| **Network** | BNB Chain |
| **Price** | $0.2031 |
| **24h Volume** | $9.02M |
| **Liquidity** | $143.3K |
| **Volume / Liquidity** | 63.0× |
| **Token Age** | 9h |
| **Top-10 Holders** | 90.8% of supply |
| **Buy / Sell Tax** | 4.0% / 4.0% |
| **24h Transactions** | 13690 buys / 1736 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xb140f8913c6da2efca0b2da7ba2178de26ff9902)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grok-bot-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
