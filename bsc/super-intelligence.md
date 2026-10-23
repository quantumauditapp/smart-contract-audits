---
token: Super Intelligence
ticker: 超脑
network: bsc
risk_score: 50
status: medium
date: 2026-10-23
---

# Super Intelligence (超脑) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/super-intelligence-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with custom tax and migration logic. The contract ownership has been renounced on-chain, effectively disabling all privileged administrative functions. The architecture is immutable, and the token logic is fixed, providing high security against unauthorized state changes.

> **Final Recommendation:** The protocol is in a secure, immutable state. No further action is required as the renounced ownership prevents any administrative interference with the token's logic or economic parameters. Users should verify the token address against official documentation to ensure they are interacting with the correct clone instance.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin libraries for ERC-20 and EIP-712 functionality, ensuring robust compliance with token standards. 7.1 Architecture is based on a secure minimal clone… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic parameters are currently fixed due to the renounced ownership, preventing any further manipulation of tax or migration states. 7.5 Governance is non-existent as the contract is fully… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are impossible for this contract as it is deployed as an EIP-1167 minimal clone. The implementation address is hardcoded into the proxy bytecode, ensuring the logic cannot be altered.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x2d6c…043c — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $8K (DexScreener, all pools). 24h trading volume $376K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 77.5% of supply. What remains: 18.1% in wallets, 59.4% in other contracts. 297 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

297 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $8K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf29d...7777`](https://bscscan.com/address/0xf29d978fffb456ff4b91b1c20d3e42696cb07777) |
| **Network** | BNB Chain |
| **Price** | $0.00000798 |
| **24h Volume** | $338.1K |
| **Liquidity** | $8.1K |
| **Volume / Liquidity** | 41.9× |
| **Token Age** | 4h |
| **Top-10 Holders** | 77.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2645 buys / 2522 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x5f331318e6288c33aeef3d286ec52d1ada8b0793)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/super-intelligence-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
