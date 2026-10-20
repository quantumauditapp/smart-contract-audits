---
token: GROKLET
ticker: GROKLET
network: ethereum
risk_score: 23
status: low
date: 2026-10-18
---

# GROKLET (GROKLET) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/groklet-eth)

---

## Audit Summary

The groklet token is an ERC-20 compliant contract with renounced ownership, enhancing decentralization by making owner-restricted functions dormant. While core ERC-20 functions are standard, a specific 'ownerOrAuthorized' address retains the ability to modify transaction and wallet size limits, which is identified as a low-severity concern. The contract is not upgradeable, eliminating upgrade-related risks.

> **Final Recommendation:** Token holders should be aware that while contract ownership is renounced, a specific 'ownerOrAuthorized' address retains the ability to modify or remove transaction and wallet size limits via the `removeLimit` function. It is recommended to understand who controls this 'ownerOrAuthorized' address and its operational policies. For enhanced security and decentralization, consider implementing a multi-signature wallet for such critical administrative roles or removing the ability to change these limits entirely if they are intended to be immutable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The groklet contract implements standard ERC-20 functionality (7.1 Architecture), with `transfer` and `transferFrom` correctly overriding the base `_transfer` logic. The contract includes mechanisms… |
| **Governance / Economics** | 10/10 | Low | Ownership of the contract has been renounced (7.3 Access Control), meaning the original owner can no longer call `onlyOwner` functions like `manualTokenSend` or `manualETHSend`, rendering them… |
| **Upgrades** | 10/10 | Low | The groklet contract is not implemented as an upgradeable proxy (7.7 Upgrades). Therefore, its logic cannot be changed after deployment, eliminating upgrade-related risks. Any future modifications to… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `CP-08` — A privileged address can change transfer or wallet limits  *(Severity: Low · Status: Unresolved)*

Numeric limits checked in the transfer path (maximum transaction or wallet size, thresholds) can be changed by a privileged function. Functions: removeLimit. Restricted to: authorized, ownerorauthorized.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 72.9% of supply. Of that, 6.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.7% in wallets, 60.6% in other contracts. 411 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

411 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $59K (DexScreener, all pools). 24h trading volume $444K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $59K of DEX liquidity across 2 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7878...8adc`](https://etherscan.io/address/0x787873c9ae96855bdb032f6ff1ef76a5e1fc8adc) |
| **Network** | Ethereum |
| **Price** | $0.0004409 |
| **24h Volume** | $444.1K |
| **Liquidity** | $59.0K |
| **Volume / Liquidity** | 7.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | 72.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1218 buys / 775 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x93f3923cf4eb2dd4cfd3beef42fc6d3178412121)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/groklet-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-18*
