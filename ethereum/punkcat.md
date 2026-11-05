---
token: PUNKCAT
ticker: PCAT
network: ethereum
risk_score: 22
status: low
date: 2026-11-05
---

# PUNKCAT (PCAT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/punkcat-eth)

---

## Audit Summary

The MemecoinToken is a standard ERC-20 implementation utilizing OpenZeppelin's audited libraries. The contract lacks any privileged roles, administrative backdoors, or complex logic, resulting in a highly secure and immutable token structure. No vulnerabilities were identified during the static analysis of the codebase.

> **Final Recommendation:** The contract is secure and requires no immediate remediation. Users should verify the token address against official sources before interacting to ensure they are engaging with the correct deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows standard ERC-20 patterns, ensuring 7.1 Architecture and 7.2 Code Security compliance. The implementation relies on battle-tested OpenZeppelin contracts, minimizing the attack… |
| **Governance / Economics** | 9/10 | Low | The token operates as a pure utility asset with no 7.4 Economic or 7.5 Governance mechanisms. There are no minting, burning, or fee-on-transfer features that could impact market stability. 7.8… |
| **Upgrades** | 10/10 | Low | The contract is not a proxy and does not support 7.7 Upgrades. This ensures long-term immutability and prevents any possibility of logic changes post-deployment. The lack of upgradeability is a… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 61.8% of supply. Of that, 24.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 13.7% in wallets, 23.6% in other contracts. 107 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

107 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $129K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat). Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $22K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x56d4...37c0`](https://etherscan.io/address/0x56d45670b89a0b45f9bcf02b2794ff312f5f37c0) |
| **Network** | Ethereum |
| **Price** | $0.00003418 |
| **24h Volume** | $129.2K |
| **Liquidity** | $22.2K |
| **Volume / Liquidity** | 5.8× |
| **Token Age** | 3h |
| **Top-10 Holders** | 61.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 318 buys / 225 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x39e30de6cbacb14ee30ddcafa107f0fcabbff011)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/punkcat-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
