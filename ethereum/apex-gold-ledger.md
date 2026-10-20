---
token: Apex Gold Ledger
ticker: AGL
network: ethereum
risk_score: 43
status: medium
date: 2026-10-02
---

# Apex Gold Ledger (AGL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/apex-gold-ledger-eth)

---

## Audit Summary

The AGL token contract implements standard ERC-20 functionality and includes a one-time `openTrading` function for liquidity pool initialization. Ownership is retained by an EOA, granting administrative control over key setup processes. No critical or high-severity vulnerabilities were identified during this audit.

> **Final Recommendation:** Ensure the private key for the owner address is secured with best practices, as it controls critical administrative functions and the initial liquidity launch. Thoroughly test the `openTrading` function parameters in a simulated environment before deployment to prevent any unintended pool configurations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements the ERC-20 standard correctly, ensuring reliable token transfers and approvals (7.2 Code Security). The `openTrading` function includes robust checks for launch conditions… |
| **Governance / Economics** | 2/10 | High | The contract is `Ownable`, meaning an external account (EOA) retains full control over administrative functions such as `transferOwnership` and `renounceOwnership` (7.3 Access Control). The owner is… |
| **Upgrades** | 5/10 | Medium | The AGL contract is not designed as an upgradeable proxy (7.7 Upgrades). This eliminates risks associated with proxy patterns, such as upgradeability misconfigurations or logic errors introduced… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 62.9% of supply. What remains: 37.6% in wallets, 25.3% in other contracts. 397 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

397 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $832K (DexScreener, all pools). 24h trading volume $956K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $832K of DEX liquidity across 9 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6340...d1c2`](https://etherscan.io/address/0x63401cdd577478f9389a1683e866a937f072d1c2) |
| **Network** | Ethereum |
| **Price** | $0.002139 |
| **24h Volume** | $953.3K |
| **Liquidity** | $832.1K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 22h |
| **Top-10 Holders** | 62.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1257 buys / 190 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x02a13b057643e001f9436fa86e3c28945b6c4475a34e068df5c6ab4d42ff93bf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/apex-gold-ledger-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-02*
