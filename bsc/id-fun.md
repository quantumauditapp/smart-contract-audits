---
token: ID FUN
ticker: IF
network: bsc
risk_score: 41
status: medium
date: 2026-10-23
---

# ID FUN (IF) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/id-fun-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with custom migration and tax logic. The contract ownership has been renounced on-chain, rendering the privileged migration functions dormant and immutable. The architecture is standard for upgradeable-style tokens, though the contract itself is not upgradeable due to the nature of minimal clones.

> **Final Recommendation:** The contract is currently in a secure, immutable state due to the renouncement of ownership. No further action is required for the current deployment. Users should note that the migration logic is permanently disabled, ensuring the current tax and anti-farmer parameters remain fixed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a robust EIP-1167 minimal clone pattern, ensuring consistent logic execution. 7.1 Architecture and 7.2 Code Security are well-implemented, adhering to standard OpenZeppelin… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance risks are minimal as the contract is immutable. The migration functions, which could have altered token economics, are no longer callable. The protocol operates as a… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the contract is a minimal clone. The implementation is locked at the bytecode level, preventing any future logic changes. This provides high security against… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 59.4% of supply. What remains: 18.1% in wallets, 41.3% in other contracts. The deployer/owner wallet itself holds 52.7%. A holder that also controls the contract can sell into its own liquidity. 137 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

137 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $96K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x83d6...7777`](https://bscscan.com/address/0x83d655df2047c3ac16232dbc1ae4a76a85167777) |
| **Network** | BNB Chain |
| **Price** | $0.00001752 |
| **24h Volume** | $96.2K |
| **Liquidity** | $17.3K |
| **Volume / Liquidity** | 5.6× |
| **Token Age** | 1h |
| **Top-10 Holders** | 59.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 919 buys / 945 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xa27912e0ed41e8dba0478fe2efb7b1e3ce35d7d3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/id-fun-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
