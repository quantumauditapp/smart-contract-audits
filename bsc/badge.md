---
token: Badge
ticker: BADGE
network: bsc
risk_score: 36
status: medium
date: 2026-10-21
---

# Badge (BADGE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/badge-bsc)

---

## Audit Summary

The protocol implements a bonding curve mechanism for token launches with automatic graduation to Uniswap V3. The architecture is modular and utilizes standard OpenZeppelin libraries. The primary risks involve potential slippage during graduation and reliance on external V3 pool configurations.

> **Final Recommendation:** The protocol is well-structured. We recommend adding a circuit breaker mechanism to the graduation process to prevent potential pool initialization failures in extreme market conditions. Ensure that the V3 pool fee tier remains consistent with the liquidity provider's expectations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The codebase demonstrates strong adherence to security best practices, including the use of ReentrancyGuard and SafeERC20. 7.1 Architecture is sound, utilizing a factory-pattern for isolated token… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic logic relies on a fixed bonding curve constant K, which is robust against simple manipulation. 7.5 Governance is currently non-existent as the protocol is immutable and automated. The… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not supported as the contracts are designed to be immutable. This eliminates risks associated with proxy admin takeovers or malicious implementation updates. The factory pattern… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 2 Low · ⚪ 5 Informational_

### `M-01` — Slippage Risk during Graduation  *(Severity: Medium · Status: Unresolved)*

The graduation process uses a hardcoded slippage tolerance (0.01%) for V3 liquidity provision, which may fail during periods of high volatility.

**Recommendation:** Implement a configurable slippage parameter for the graduation process.


### `M-02` — Lack of Emergency Withdrawals  *(Severity: Medium · Status: Unresolved)*

If the graduation fails or the pool becomes unusable, funds may be trapped in the locker contract.

**Recommendation:** Add an emergency recovery function restricted to a multi-sig or DAO.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x85f8…6f64 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `L-01` — Metadata URI Immutability  *(Severity: Low · Status: Unresolved)*

The metadata URI is set at construction and cannot be updated, which may be problematic if the hosting service goes offline.

**Recommendation:** Consider allowing a one-time update or using a decentralized storage pointer.


### `L-02` — Unchecked Return Values  *(Severity: Low · Status: Unresolved)*

Some external calls to non-standard tokens might not revert on failure, though SafeERC20 is used for most.

**Recommendation:** Audit all external token interactions for non-standard behavior.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 31.9% of supply. Of that, 2.0% burned, 10.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 17.9% in wallets, 1.9% in other contracts. 579 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

579 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $39K (DexScreener, all pools). 24h trading volume $522K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner key. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $39K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdf37...aaaa`](https://bscscan.com/address/0xdf37d7e27061109b7ba94480e938e7e66ae9aaaa) |
| **Network** | BNB Chain |
| **Price** | $0.0001572 |
| **24h Volume** | $522.3K |
| **Liquidity** | $38.9K |
| **Volume / Liquidity** | 13.4× |
| **Token Age** | 6h |
| **Top-10 Holders** | 31.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3114 buys / 2496 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xcf4a27eb7ef1f082ed3a8f32446854c0eceb4b5c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/badge-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
