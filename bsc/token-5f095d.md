---
token: フリーダム・オブ・マネー
ticker: フリーダム・オブ・マネー
network: bsc
risk_score: 1
status: low
date: 2026-10-20
---

# フリーダム・オブ・マネー (フリーダム・オブ・マネー) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-5f095d-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone token deployed on BSC. The contract implements standard ERC-20 functionality with additional tax and migration logic. Ownership has been renounced on-chain, effectively disabling all privileged administrative functions. The architecture is immutable, and the code follows standard OpenZeppelin patterns for upgradeable contracts, though the clone pattern prevents actual upgrades.

> **Final Recommendation:** The protocol is in a secure, immutable state due to the renouncement of ownership. No further action is required for the current implementation as the privileged functions are dormant and the contract logic is fixed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a robust EIP-1167 minimal clone architecture, ensuring consistent logic across deployments. 7.1 Architecture and 7.2 Code Security are well-implemented, adhering to standard… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance risks are minimal due to the renounced ownership status. The migration logic, which previously allowed for tax enforcement, is now permanently locked. No entity can… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the contract is a minimal clone with fixed implementation logic. The use of Initializable base contracts is appropriate for the clone pattern and does not introduce… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 25.4% of supply. Of that, 4.8% burned, 8.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.1% in wallets, 3.2% in other contracts. 3,321 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,321 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $56K (DexScreener, all pools). 24h trading volume $536K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 3.9% on sell. Market: $56K of DEX liquidity across 2 pools. Launch: 3 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x097d...7777`](https://bscscan.com/address/0x097dd7ee96b36444ad3439b32a8518e682ff7777) |
| **Network** | BNB Chain |
| **Price** | $0.0003099 |
| **24h Volume** | $534.8K |
| **Liquidity** | $56.3K |
| **Volume / Liquidity** | 9.5× |
| **Token Age** | 3d |
| **Top-10 Holders** | 25.4% of supply |
| **Buy / Sell Tax** | 3.0% / 3.9% |
| **24h Transactions** | 7137 buys / 2619 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x3f1092993e74ce39eea28b3bf9a1c33b66fe27cb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-5f095d-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
