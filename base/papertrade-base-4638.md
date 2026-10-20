---
token: Papertrade
ticker: PAPER
network: base
risk_score: 57
status: medium
date: 2026-10-19
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base-4638)

---

## Audit Summary

The ClankerToken contract is an ERC-20 token with standard functionalities, including burning, voting, and cross-chain transfer capabilities. The audit identified high and medium severity issues related to privileged control over token supply and individual balances, specifically through cross-chain minting and burning functions controlled by a designated bridge address. The contract leverages well-established OpenZeppelin libraries, contributing to its foundational security.

> **Final Recommendation:** It is crucial to ensure that the private keys controlling the `SuperchainTokenBridge` address and the `_admin` address are secured with the highest possible standards, such as multi-signature wallets. Implement robust operational procedures and monitoring for all privileged functions, especially `crosschainMint` and `crosschainBurn`, to prevent unauthorized or malicious use. Consider implementing time-locks or additional governance checks for critical actions if feasible.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The ClankerToken contract implements standard ERC-20 functionalities, inheriting from robust OpenZeppelin libraries for features like burning, voting, and permits, which generally contribute to code… |
| **Governance / Economics** | 1/10 | High | The token incorporates ERC20Votes, enabling governance participation for token holders. However, the economic stability (7.4 Economic) of the token is significantly impacted by the centralized… |
| **Upgrades** | 5/10 | Medium | The ClankerToken contract is not implemented as an upgradeable proxy (7.7 Upgrades), meaning its core logic cannot be changed post-deployment. This reduces the risk associated with upgrade… |

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


### `CP-01` — A privileged address can mint new tokens  *(Severity: Informational · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: crosschainMint(address,uint256). Ownership is renounced, so no one can call these functions now.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `CP-02` — A privileged address can change holders' balances  *(Severity: Informational · Status: Unresolved)*

A privileged function writes other holders' balances directly — it can burn or move tokens out of any address it targets. Functions: crosschainBurn(address,uint256). Ownership is renounced, so no one can call these functions now.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 5,039 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,039 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.2M (DexScreener, all pools). 24h trading volume $42.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.2M of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3e19...fb07`](https://basescan.org/address/0x3e199f015ea827f27c2671f8eae516b8944ffb07) |
| **Network** | Base |
| **Price** | $0.000101 |
| **24h Volume** | $42.54M |
| **Liquidity** | $10.20M |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 22h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3165 buys / 2973 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x8dd7fcbe2e3c4c928e746d08919b530de47a4b99)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base-4638)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
