---
token: Papertrade
ticker: PAPER
network: base
risk_score: 52
status: medium
date: 2026-11-07
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 52/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base-612a)

---

## Audit Summary

The ClankerToken is a standard ERC-20 implementation with cross-chain capabilities integrated via the Superchain Token Bridge. The architecture relies on the bridge contract to manage supply across chains, which introduces centralized control points. While the code follows standard OpenZeppelin patterns, the ability for the bridge to burn tokens from any address represents a significant trust requirement.

> **Final Recommendation:** The protocol should ensure that the Superchain Token Bridge address is correctly configured and monitored for any anomalous activity. Given the high-privilege nature of the bridge, implementing a multi-signature or timelock mechanism for administrative updates to the admin address is recommended to prevent unauthorized configuration changes.

Users should be aware that the token supply is dynamic and controlled by the bridge. Regular audits of the bridge contract itself are essential, as the security of the ClankerToken is directly tied to the integrity of the cross-chain messaging and bridge execution logic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes robust OpenZeppelin libraries for ERC-20, Votes, and Permit functionality, ensuring standard compliance. 7.1 Architecture is well-defined for cross-chain interoperability, and… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risks are present due to the minting capability, which can dilute token holders if the bridge is compromised. 7.5 Governance is centralized through an admin role capable of updating… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not natively implemented in this contract, as it is a non-proxy deployment. 7.8 Operations are straightforward, with no complex state transitions outside of the bridge-controlled… |

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

The crosschainMint function allows the Superchain Token Bridge to create new tokens at any time. This increases the total supply and dilutes the value held by existing token holders. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure that the bridge contract is secured and that minting events are monitored by the community to detect unexpected supply inflation.


### `CP-02` — Privileged Balance Modification  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the Superchain Token Bridge to remove tokens from any user's balance. This grants the bridge controller the power to effectively seize or destroy tokens held by any address. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Restrict the use of burn operations to only those initiated by the token owner or strictly defined cross-chain protocols, and implement transparency logs for all burn actions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 5,337 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,337 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.3M (DexScreener, all pools). 24h trading volume $64.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.3M of DEX liquidity across 1 pools. Launch: 365 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x013d...db07`](https://basescan.org/address/0x013d4ccd61f996202bfbcb41392845eb6904db07) |
| **Network** | Base |
| **Price** | $0.000102 |
| **24h Volume** | $64.22M |
| **Liquidity** | $10.33M |
| **Volume / Liquidity** | 6.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1449 buys / 1401 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xa14a3e5b8f5b0c83ab3a623c802feb653f29b22b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base-612a)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
