---
token: wkeyDA03
ticker: WKEYDA03
network: bsc
risk_score: 42
status: medium
date: 2026-11-02
---

# wkeyDA03 (WKEYDA03) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wkeyda03-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with tax-enforced transfer logic. The contract ownership has been renounced on-chain, rendering the administrative migration functions (startMigration, finalizeMigration) permanently inaccessible. The code follows standard OpenZeppelin patterns for upgradeable contracts, though the deployment as a minimal clone makes it immutable.

> **Final Recommendation:** The protocol is in a secure, immutable state due to the renunciation of ownership. No further action is required for the current deployment as the administrative functions are effectively disabled.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes EIP-1167 minimal clones to ensure gas-efficient deployment. Code security is robust, leveraging standard OpenZeppelin libraries for ERC-20 and EIP-712 compliance. 7.1… |
| **Governance / Economics** | 5/10 | Medium | Economic parameters are fixed due to the renounced ownership. 7.4 Economic: Tax logic is locked in its current state. 7.5 Governance: No active governance exists as ownership is renounced. 7.8… |
| **Upgrades** | 8/10 | Low | The contract is deployed as an EIP-1167 minimal clone, which is inherently immutable. 7.7 Upgrades: No upgrade path exists for the logic contract. The implementation is fixed at the time of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.0% (≈ permanent lock) |
| **LP Locked** | 99.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 66.8% of supply. Of that, 1.5% burned, 51.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 6.4% in wallets, 7.7% in other contracts. The deployer/owner wallet itself holds 32.2%. A holder that also controls the contract can sell into its own liquidity. 297 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $270K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

297 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.0% of the pool's LP is burned or time-locked. 99.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 1.0% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 1.13% on sell. Market: $9K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x77ff...7777`](https://bscscan.com/address/0x77ffd889fa91103f68eec858c98ca53738d27777) |
| **Network** | BNB Chain |
| **Price** | $0.00000993 |
| **24h Volume** | $229.2K |
| **Liquidity** | $9.3K |
| **Volume / Liquidity** | 24.6× |
| **Token Age** | 3h |
| **Top-10 Holders** | 66.8% of supply |
| **Buy / Sell Tax** | 1.0% / 1.1% |
| **24h Transactions** | 2841 buys / 2375 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xd216827eff3594876e719d47f060d12faf70f72d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wkeyda03-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
