---
token: 国库时代
ticker: 国库时代
network: bsc
risk_score: 45
status: medium
date: 2026-10-28
---

# 国库时代 (国库时代) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-203a33-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone token implementation. The contract ownership has been renounced, effectively locking the privileged migration functions and preventing further administrative changes to the token's tax and migration state. The codebase follows standard OpenZeppelin patterns for ERC-20 and permit functionality.

> **Final Recommendation:** The protocol is currently in a secure, immutable state due to the renouncement of ownership. No further action is required for the existing deployment. Future deployments should ensure that if migration or tax logic is intended to be dynamic, ownership is managed through a secure multi-signature wallet rather than being renounced prematurely.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes a robust EIP-1167 minimal clone pattern, ensuring immutable logic deployment. 7.1 Architecture and 7.2 Code Security are well-implemented using standard library patterns.… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance risks are mitigated by the renounced ownership, preventing any centralized manipulation of tax or migration states. The token logic is fixed, providing predictability… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the contract is an immutable EIP-1167 clone. The implementation cannot be changed or redirected, ensuring long-term stability of the contract logic. No upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x14e5…be4a — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $92K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 67.6% of supply. What remains: 8.3% in wallets, 59.3% in other contracts. 15,177 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

15,177 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 2% on buy, 1.98% on sell. Market: $9K of DEX liquidity across 2 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa17d...7777`](https://bscscan.com/address/0xa17dd915b775e49d18ec9916afe7597f16427777) |
| **Network** | BNB Chain |
| **Price** | $0.00000891 |
| **24h Volume** | $69.1K |
| **Liquidity** | $9.0K |
| **Volume / Liquidity** | 7.7× |
| **Token Age** | 1d |
| **Top-10 Holders** | 67.6% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 4894 buys / 696 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xf9b23f91d31b5673a80971c0fb1c2b580dd29cab)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-203a33-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
