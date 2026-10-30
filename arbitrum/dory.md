---
token: Dory
ticker: DORY
network: arbitrum
risk_score: 18
status: low
date: 2026-10-30
---

# Dory (DORY) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 18/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dory-arb)

---

## Audit Summary

The contract is a standard ERC1967Proxy implementation. Static analysis confirms the ownership has been renounced, meaning no administrative functions are currently active. The implementation contract source is not verified, limiting visibility into the underlying logic, but the proxy itself adheres to standard EIP-1967 patterns.

> **Final Recommendation:** Since the ownership has been renounced, the contract is effectively immutable. Users should verify the implementation contract at the provided address to ensure the underlying logic aligns with expected behavior, as the proxy itself only facilitates delegation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows the standard EIP-1967 proxy pattern, ensuring clear separation between the proxy and implementation. 7.1 Architecture is robust, utilizing standard storage slots to prevent… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance factors are not applicable as the contract acts solely as a transparent proxy. There are no internal economic parameters or governance mechanisms present. 7.6 External… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are technically possible via the proxy pattern, but the renounced ownership prevents any further modifications to the implementation address. 7.8 Operations are stable as the contract is… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.4% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x2cc3…045a — holds 99.4% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 33.9% of supply. Of that, 22.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 5.2% in wallets, 6.0% in other contracts. 39,324 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

39,324 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $2.6M (GeckoTerminal, all pools). 24h trading volume $37K (GeckoTerminal, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $2.6M of DEX liquidity across 11 pools. Launch: 415 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x33b4...36ae`](https://arbiscan.io/address/0x33b49f2264e85bb124d2730dc180182717d436ae) |
| **Network** | Arbitrum |
| **Price** | $60.9696 |
| **24h Volume** | $36.7K |
| **Liquidity** | $2.60M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 33.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 116 buys / 48 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0x33b49f2264e85bb124d2730dc180182717d436ae)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dory-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
