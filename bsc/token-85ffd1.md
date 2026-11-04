---
token: 中国屌上天
ticker: 胖五
network: bsc
risk_score: 50
status: medium
date: 2026-11-04
---

# 中国屌上天 (胖五) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-85ffd1-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone implementing a standard ERC-20 token with custom migration and tax logic. The contract ownership has been renounced, effectively disabling all privileged administrative functions, including migration state changes. The architecture is immutable, and the code follows standard OpenZeppelin patterns for token functionality.

> **Final Recommendation:** The protocol is currently in a fully immutable state due to the renounced ownership. No further action is required to secure the contract logic, as the administrative functions are permanently disabled. Users should be aware that the current tax and migration state is fixed and cannot be adjusted by any entity.

Future interactions should focus on monitoring the existing state of the token to ensure it aligns with expected market behavior. Since the contract is immutable, no further security updates or patches can be applied to this specific instance.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a robust EIP-1167 minimal clone pattern, ensuring consistent logic deployment. 7.1 Architecture and 7.2 Code Security are well-implemented, adhering to established ERC-20… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are effectively mitigated by the renounced ownership status. Since the owner cannot trigger migration functions, the token's economic parameters are locked in… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the contract is an immutable minimal clone. The implementation address is fixed at deployment, preventing any future logic changes. 7.8 Operations are stable, as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xddac…308c — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $427K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 66.7% of supply. What remains: 16.5% in wallets, 50.3% in other contracts. 298 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

298 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 0.99% on sell. Market: $9K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x58b2...7777`](https://bscscan.com/address/0x58b2931f2bf31d2a6299e4f987c1d7ac6a967777) |
| **Network** | BNB Chain |
| **Price** | $0.00000972 |
| **24h Volume** | $387.8K |
| **Liquidity** | $9.3K |
| **Volume / Liquidity** | 41.9× |
| **Token Age** | 3h |
| **Top-10 Holders** | 66.7% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 3705 buys / 3769 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x5f4e19638d9b24b612a97c913b927079d7d16134)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-85ffd1-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
