---
token: Anthropic
ticker: ANTHROPIC
network: base
risk_score: 53
status: medium
date: 2026-10-31
---

# Anthropic (ANTHROPIC) — Smart Contract Security Analysis | Base

> **Risk Score: 53/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anthropic-base-43ba)

---

## Audit Summary

ClankerToken is an ERC-20 compliant token integrated with the Superchain Token Bridge for cross-chain functionality. The architecture relies on the Superchain Token Bridge to manage supply via minting and burning. While the implementation follows standard OpenZeppelin patterns, the centralized control over supply and balance manipulation via the bridge introduces significant trust requirements.

> **Final Recommendation:** Users should be aware that the Superchain Token Bridge holds significant power over the token supply and individual user balances. It is recommended to monitor the bridge's security and governance, as any compromise of the bridge contract directly impacts the token's economic stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes robust OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, leveraging standard cross-chain interfaces. 7.2 Code Security is high… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risk is centered on the bridge's ability to alter supply and individual balances. 7.5 Governance is centralized under an admin role for metadata updates. 7.6 External dependencies are… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not implemented in this version as the contract is not a proxy. 7.8 Operations are straightforward, with clear event logging for all privileged actions. No complex upgrade paths… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Privileged Minting Capability  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the Superchain Token Bridge to increase the total supply of tokens at any time, which can dilute the value of existing holdings. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure that the bridge contract is secured and its minting parameters are transparently governed to prevent unauthorized supply inflation.


### `CP-02` — Privileged Balance Manipulation  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the Superchain Token Bridge to remove tokens from any user's balance, effectively granting the bridge the power to seize or destroy user assets. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement strict circuit breakers or multi-signature requirements on the bridge contract to limit the impact of a potential compromise.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 5,239 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,239 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.3M (DexScreener, all pools). 24h trading volume $57.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.3M of DEX liquidity across 1 pools. Launch: 365 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf7b9...4cea`](https://basescan.org/address/0xf7b9cf4dab32ce42f1e08c05f561ccc0e7b44cea) |
| **Network** | Base |
| **Price** | $0.000102 |
| **24h Volume** | $56.98M |
| **Liquidity** | $10.32M |
| **Volume / Liquidity** | 5.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1463 buys / 1319 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x95b81e69cc6c2822af77d001278a054f2e318880)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anthropic-base-43ba)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
