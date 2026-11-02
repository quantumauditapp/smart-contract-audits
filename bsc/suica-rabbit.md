---
token: Suica Rabbit
ticker: うさぎ
network: bsc
risk_score: 1
status: low
date: 2026-11-02
---

# Suica Rabbit (うさぎ) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/suica-rabbit-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal proxy (EIP-1167) implementation of an ERC-20 token with custom tax and migration logic. The contract ownership has been renounced on-chain, rendering all privileged functions (startMigration, finalizeMigration) permanently inaccessible. The code follows standard OpenZeppelin patterns for upgradeable contracts, though the proxy structure itself is immutable. No critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** The protocol is currently in a secure, immutable state due to the renunciation of ownership. No further action is required to secure the contract logic. Users should verify the token address against official documentation to ensure they are interacting with the correct deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture utilizes a standard EIP-1167 minimal proxy pattern, ensuring gas efficiency and consistent logic deployment. 7.1 Architecture is sound, utilizing well-audited OpenZeppelin libraries… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance risks are mitigated by the renounced ownership status. Since the owner cannot trigger migration or tax changes, the tokenomics are effectively locked in their current… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the contract is deployed as an EIP-1167 minimal clone, which is immutable by design. The implementation address is hardcoded into the proxy bytecode, preventing any… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 27.1% of supply. Of that, 4.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.2% in wallets, 17.0% in other contracts. 3,071 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,071 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $182K (DexScreener, all pools). 24h trading volume $125K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 1% on sell. Market: $182K of DEX liquidity across 1 pools. Launch: 54 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x113d...7777`](https://bscscan.com/address/0x113d68c8cca4fe5ba25f49c00784079d168e7777) |
| **Network** | BNB Chain |
| **Price** | $0.001854 |
| **24h Volume** | $124.8K |
| **Liquidity** | $181.8K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 27.1% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 555 buys / 394 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xd6fe21107c05a153d419edc3d93072066d52dff9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/suica-rabbit-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
