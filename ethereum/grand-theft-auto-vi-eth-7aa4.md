---
token: Grand Theft Auto VI
ticker: GTA6
network: ethereum
risk_score: 0
status: low
date: 2026-11-06
---

# Grand Theft Auto VI (GTA6) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grand-theft-auto-vi-eth-7aa4)

---

## Audit Summary

The audited contract is a standard ERC-20 token implementation utilizing OpenZeppelin's battle-tested libraries. The codebase follows industry standards for token transfers and allowance management. No privileged functions or administrative backdoors were identified, ensuring a decentralized and trustless operation.

> **Final Recommendation:** The contract is secure and ready for deployment as a standard utility token. No further code changes are required for security purposes.

Users should ensure that any future integrations with this token verify the contract address against the official deployment to avoid interaction with unauthorized clones.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture strictly adheres to the ERC-20 standard, ensuring compatibility with all major DeFi protocols. 7.1 Architecture is clean and modular, leveraging inherited libraries for 7.2 Code… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance factors are not applicable as the contract lacks minting, burning, or administrative governance mechanisms. The token supply is fixed upon deployment, preventing… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not supported by this contract, as it is a standard immutable implementation. This eliminates 7.8 Operations risks associated with proxy upgrades or malicious logic updates. The… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 19.4% of supply. What remains: 11.6% in wallets, 7.8% in other contracts. 257 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

257 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $56K (DexScreener, all pools). 24h trading volume $407K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $56K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x684a...4a51`](https://etherscan.io/address/0x684ac37cbed24f8d3b3e67c0df627747f1a04a51) |
| **Network** | Ethereum |
| **Price** | $0.000372 |
| **24h Volume** | $406.5K |
| **Liquidity** | $55.5K |
| **Volume / Liquidity** | 7.3× |
| **Token Age** | 1d |
| **Top-10 Holders** | 19.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 371 buys / 146 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xf8153a86966c510b0214e2b61a91218ce255e1d782dcebe0ce30840672508192)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grand-theft-auto-vi-eth-7aa4)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
