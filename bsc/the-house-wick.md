---
token: The House Wick
ticker: WICK
network: bsc
risk_score: 84
status: high
date: 2026-10-20
---

# The House Wick (WICK) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-house-wick-bsc)

---

## Audit Summary

The Wick protocol is an ERC-20 token with integrated rebase and swapback mechanisms. While ownership of the contract has been renounced, the protocol relies on a 'KEEPER' address that maintains significant control over transfer rules, fees, and oracle-based state transitions. The audit identified a critical vulnerability regarding arbitrary ETH transfers and medium-risk concerns regarding centralized control over token economics.

> **Final Recommendation:** The protocol should immediately address the critical ETH payout vulnerability by implementing strict access controls or reentrancy guards on all external-facing payout functions. It is recommended to transition the KEEPER role to a multi-signature wallet or a decentralized DAO to mitigate the risks associated with centralized control over economic parameters.

Furthermore, ensure that all state-changing functions are thoroughly tested against edge cases in the oracle feed, as the current implementation relies heavily on the accuracy and availability of the external price data to prevent unexpected rebase behavior.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture utilizes standard OpenZeppelin libraries for reentrancy protection and ERC-20 compliance. 7.1 Architecture: The contract implements a custom rebase and swapback logic triggered by a… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic: The protocol relies on a keeper to trigger rebases and fee distributions, creating a dependency on an external actor. 7.5 Governance: There is no decentralized governance mechanism; the… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: The contract is not upgradeable, which provides security against malicious logic changes post-deployment. The lack of proxy patterns ensures that the code deployed is the code that… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, PinkLock02 |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Arbitrary ETH Transfer Vulnerability  *(Severity: High · Status: Unresolved)*

The _payout function allows for the transfer of ETH to addresses that can be influenced by the caller. This could potentially allow a malicious actor to drain contract funds if the payout logic is triggered under specific conditions.

**Recommendation:** Implement strict validation on the recipient address and ensure that the payout logic is protected against reentrancy and unauthorized access.


### `CP-05` — Centralized Control Over Transfer Functionality  *(Severity: Medium · Status: Unresolved)*

The keeper address has the power to toggle switches that determine whether transfers or sales are permitted. This allows the keeper to effectively freeze user funds or halt trading at will.

**Recommendation:** Consider implementing a time-lock or a decentralized voting mechanism for actions that can halt protocol functionality.


### `CP-07` — Keeper Control Over Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The keeper can modify the transfer fees applied to transactions. This grants the keeper the ability to unilaterally change the economic cost of using the token.

**Recommendation:** Define a maximum fee cap in the contract code to prevent the keeper from setting exorbitant fees.


### `CP-08` — Keeper Control Over Transaction Limits  *(Severity: Low · Status: Unresolved)*

The keeper can change transaction or wallet size limits, which directly impacts the liquidity and accessibility of the token for users.

**Recommendation:** Document these limits clearly and consider setting hard-coded boundaries that the keeper cannot exceed.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.5% of supply. Of that, 56.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 8.8% in wallets, 15.3% in other contracts. 101 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

101 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 20 Oct 2027 (364 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $37K (DexScreener, all pools). 24h trading volume $100K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 5% on buy, 5% on sell. Market: $37K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbc47...70bc`](https://bscscan.com/address/0xbc4721b16eec6197496524ea0d8082ab08a470bc) |
| **Network** | BNB Chain |
| **Price** | $0.0000326 |
| **24h Volume** | $100.0K |
| **Liquidity** | $37.0K |
| **Volume / Liquidity** | 2.7× |
| **Token Age** | 13h |
| **Top-10 Holders** | 80.5% of supply |
| **Buy / Sell Tax** | 5.0% / 5.0% |
| **24h Transactions** | 582 buys / 407 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x8197cff7362c57da2947478fef5cf8b9d43ac390)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-house-wick-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
