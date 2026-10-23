---
token: Flying Tesla Roadster
ticker: FTR
network: bsc
risk_score: 18
status: low
date: 2026-10-23
---

# Flying Tesla Roadster (FTR) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 18/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/flying-tesla-roadster-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone implementation of an ERC-20 token with custom tax and migration logic. The contract ownership has been renounced on-chain, effectively disabling all administrative functions, including migration controls. The architecture is immutable, and the code adheres to standard OpenZeppelin upgradeable patterns, though the renounced ownership renders the upgradeable features dormant.

> **Final Recommendation:** The protocol is currently in a state of permanent immutability due to the renounced ownership. No further security actions are required regarding administrative functions as they are effectively disabled. Users should be aware that the current tax and migration state is final and cannot be adjusted by any party.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a robust EIP-1167 minimal clone pattern, ensuring consistent logic deployment. 7.1 Architecture and 7.2 Code Security are sound, leveraging well-audited OpenZeppelin libraries.… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance parameters are locked due to the renounced ownership. The migration mechanism, intended to shift pool states, is no longer accessible, preventing any further… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are effectively disabled for this instance. While the contract inherits from Initializable and uses upgradeable base contracts, the EIP-1167 clone pattern fixes the implementation… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 18.4% |
| **LP Locked** | 18.4% — Null Address |
| **Top-1 Unlocked Holder** | ⚠️ 81.6% |
| **Top-3 Unlocked** | ⚠️ 81.6% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

18.4% of the pool's LP is burned or time-locked. 18.4% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 81.6% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xbd4e…89b1 — holds 81.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 8.8% of supply. Of that, 0.2% burned, 0.2% locked, 7.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 1.0% in wallets, 0.5% in other contracts. 11,901 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

11,901 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.8M (DexScreener, all pools). 24h trading volume $389K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $1.8M of DEX liquidity across 1 pools. Launch: 7 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 7 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 7 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x66e0...7777`](https://bscscan.com/address/0x66e0bf5ea20ca8386ac370026ca7a4db32417777) |
| **Network** | BNB Chain |
| **Price** | $0.0125 |
| **24h Volume** | $389.2K |
| **Liquidity** | $1.76M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 7d |
| **Top-10 Holders** | 8.8% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 1644 buys / 917 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x86d482b68f04950c692db6b519c045fc7ea90247)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/flying-tesla-roadster-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
