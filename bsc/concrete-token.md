---
token: Concrete Token
ticker: CT
network: bsc
risk_score: 58
status: medium
date: 2026-10-03
---

# Concrete Token (CT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/concrete-token-bsc)

---

## Audit Summary

The audit reviewed the ConcreteTokenOFT contract, deployed as a UUPS proxy on BSC. The contract functions as an ERC-20 token with LayerZero OFT capabilities, enabling cross-chain transfers. Ownership is managed by a 2/3 multisig. No specific vulnerabilities were identified in the provided code map.

> **Final Recommendation:** Maintain strict security practices for the multisig wallet controlling the contract, ensuring all signers are aware of their responsibilities and follow secure key management protocols. Implement a robust upgrade process that includes thorough testing, independent audits, and transparent communication for any proposed contract changes. Continuously monitor external dependencies, particularly the LayerZero endpoint, for any security announcements or required updates (7.6 External, 7.8 Operations).

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The ConcreteTokenOFT contract implements the ERC-20 standard and LayerZero's Omnichain Fungible Token (OFT) functionality, allowing for seamless cross-chain token transfers (7.1 Architecture).… |
| **Governance / Economics** | 3/10 | High | The contract's ownership is retained and managed by a 2/3 multisig wallet, enhancing security for critical administrative actions (7.5 Governance). The owner has significant control over the… |
| **Upgrades** | 2/10 | High | The ConcreteTokenOFT contract is designed as an upgradeable UUPS proxy, allowing for future modifications and bug fixes (7.7 Upgrades). The owner, a 2/3 multisig, is responsible for initiating and… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 57.0% |
| **Top-3 Unlocked** | ⚠️ 99.2% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 5 address(es) other than the owner/deployer. One of them — a wallet, 0x42aa…705e — holds 57.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 79% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 81.5% of supply. What remains: 43.7% in wallets, 37.9% in other contracts. 20,054 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Concrete (CT). 20,054 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $98K (DexScreener, all pools). 24h trading volume $239.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $268K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a 2-of-3 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $98K of DEX liquidity across 8 pools. Launch: 3 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0a09...7f46`](https://bscscan.com/address/0x0a092e544da31150b439a1aaa1a3a2214a867f46) |
| **Network** | BNB Chain |
| **Price** | $0.5212 |
| **24h Volume** | $263.2K |
| **Liquidity** | $77.6K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 3d |
| **Top-10 Holders** | 81.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1192 buys / 1223 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x4f1c8be4685db434e645f04b811780a82b2331bc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/concrete-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*
