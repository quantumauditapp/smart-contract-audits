---
token: 派大星国旗
ticker: 派大星
network: bsc
risk_score: 32
status: low
date: 2026-10-22
---

# 派大星国旗 (派大星) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 32/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-211f16-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone implementation of an ERC-20 token with migration-based state transitions. The contract ownership has been renounced on-chain, effectively disabling all privileged administrative functions. The architecture is immutable, and the token logic is fixed, providing a high degree of security against unauthorized state changes.

> **Final Recommendation:** The contract is in a secure, immutable state. No further action is required for security hardening as the administrative surface area has been permanently removed via ownership renouncement. Users should continue to monitor the token's market activity and liquidity pool health, as these are the only remaining vectors for economic impact.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a standard EIP-1167 minimal clone pattern, ensuring consistent logic across deployments. 7.1 Architecture is robust due to the immutable nature of the clone. 7.2 Code Security… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance parameters are currently frozen due to the renounced ownership. No further changes to the migration state or tax logic can be initiated by any party. This eliminates… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are not possible for this deployment. As an EIP-1167 minimal clone, the implementation address is hardcoded into the bytecode. This provides maximum security against proxy-based upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xddac…308c — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 41.3% of supply. What remains: 12.2% in wallets, 29.1% in other contracts. 402 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

402 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $347K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 0.99% on sell. Market: $17K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe340...7777`](https://bscscan.com/address/0xe3405f29db98173b3eb0b620ba5567da4e947777) |
| **Network** | BNB Chain |
| **Price** | $0.0000355 |
| **24h Volume** | $300.1K |
| **Liquidity** | $16.7K |
| **Volume / Liquidity** | 17.9× |
| **Token Age** | 4h |
| **Top-10 Holders** | 41.3% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 2732 buys / 2448 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xae02c1cd9a9ee763fac72b27fe3179cc3cd2a291)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-211f16-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
