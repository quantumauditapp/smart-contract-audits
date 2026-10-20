---
token: saucecoin
ticker: SAUCE
network: bsc
risk_score: 12
status: low
date: 2026-10-19
---

# saucecoin (SAUCE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/saucecoin-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an EIP-1167 minimal clone, functioning as an ERC-20 token. Ownership has been renounced, rendering all owner-restricted functions, including those that modify transfer fees, permanently inactive. No critical vulnerabilities were identified.

> **Final Recommendation:** Given the renounced ownership and the non-upgradeable nature of the EIP-1167 minimal clone, the FlapTaxTokenV3 contract exhibits a high degree of immutability and decentralized control. Token holders should be aware that no administrative functions can be invoked to change the token's behavior, including its fee structure. It is recommended to ensure all external integrations and user interfaces accurately reflect this immutable state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The FlapTaxTokenV3 contract implements the ERC-20 standard, providing essential token functionalities such as `transfer`, `balanceOf`, and `approve`. It is deployed as an EIP-1167 minimal clone… |
| **Governance / Economics** | 7/10 | Low | The governance and economic risk profile of FlapTaxTokenV3 is significantly reduced due to the renounced ownership. The `owner` role, which previously controlled critical functions like… |
| **Upgrades** | 9/10 | Low | The FlapTaxTokenV3 contract is deployed as an EIP-1167 minimal clone, which means its implementation is fixed at deployment and cannot be upgraded or modified (7.7 Upgrades). While it inherits… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x1584…cb02 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 14.2% of supply. What remains: 6.4% in wallets, 7.8% in other contracts. 6,110 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

6,110 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $243K (DexScreener, all pools). 24h trading volume $547K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $243K of DEX liquidity across 3 pools. Launch: 59 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd7cc...7777`](https://bscscan.com/address/0xd7ccd29b6fd1464edb425f24b01115556e737777) |
| **Network** | BNB Chain |
| **Price** | $0.003788 |
| **24h Volume** | $546.5K |
| **Liquidity** | $243.4K |
| **Volume / Liquidity** | 2.2× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 14.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3731 buys / 3394 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x08c96d501c699fab7ffce8a730a431393045efc1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/saucecoin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
