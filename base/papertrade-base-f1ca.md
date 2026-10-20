---
token: Papertrade
ticker: PAPER
network: base
risk_score: 54
status: medium
date: 2026-10-20
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base-f1ca)

---

## Audit Summary

The ClankerToken is an ERC-20 compliant token designed for cross-chain interoperability via the Superchain Token Bridge. The architecture relies on standard OpenZeppelin libraries for core functionality, including voting and permit features. While the implementation is robust, the protocol grants significant power to the bridge contract, which introduces centralized risks regarding token supply and user balances.

> **Final Recommendation:** The protocol should ensure that the Superchain Token Bridge address is correctly configured and that the bridge itself is subject to rigorous security audits, as it holds the authority to modify token balances. Users should be aware that the bridge acts as a privileged controller over the token supply.

Maintain strict monitoring of the admin address to prevent unauthorized metadata or administrative changes. No further code changes are required for the current implementation, as the identified risks are inherent to the cross-chain bridge architecture.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard, well-audited OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture follows standard cross-chain patterns, while 7.2 Code Security is… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risks are present due to the ability of the bridge to mint and burn tokens, which directly impacts supply and holder balances. 7.5 Governance is centralized under the admin role for… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not implemented via proxy patterns in this contract. The contract is immutable in its current deployment. 7.8 Operations are straightforward, with no complex state-changing logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 7 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Privileged Minting Authority  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the designated bridge contract to create new tokens at will, which increases the total supply and dilutes existing token holders. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure the bridge contract is secured with multi-signature requirements or timelocks to prevent unauthorized minting events.


### `CP-02` — Privileged Balance Manipulation  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the bridge contract to remove tokens from any user's balance, effectively granting it the power to seize or destroy user assets. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement strict circuit breakers or monitoring on the bridge contract to detect and halt anomalous burn activity.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 5,312 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,312 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.3M (DexScreener, all pools). 24h trading volume $54.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.3M of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb355...7b07`](https://basescan.org/address/0xb3552eefaf0f94fd82a49b745a1c46a45c897b07) |
| **Network** | Base |
| **Price** | $0.000102 |
| **24h Volume** | $54.80M |
| **Liquidity** | $10.30M |
| **Volume / Liquidity** | 5.3× |
| **Token Age** | 2h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1408 buys / 1178 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x5cb3bcb56b5145398cee3225c3268b9b95562dd4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base-f1ca)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
