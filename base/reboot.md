---
token: Reboot
ticker: REBOOT
network: base
risk_score: 52
status: medium
date: 2026-11-03
---

# Reboot (REBOOT) — Smart Contract Security Analysis | Base

> **Risk Score: 52/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/reboot-base)

---

## Audit Summary

The ClankerToken is a standard ERC-20 implementation with additional cross-chain functionality via the Superchain Token Bridge. The architecture relies on the bridge contract to manage minting and burning operations. While the core logic follows standard OpenZeppelin patterns, the centralized control over token supply via the bridge presents a significant trust requirement for users.

> **Final Recommendation:** The protocol should ensure that the Superchain Token Bridge is secured with multi-signature wallets or timelocks to mitigate the risk of unauthorized minting or burning. Regular monitoring of the bridge's administrative actions is recommended to ensure transparency for token holders.

Users should acknowledge that the token supply is dynamic and controlled by the bridge. We recommend documenting the specific bridge address and the governance process for any future changes to the administrative roles.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, separating cross-chain logic from standard token operations. 7.2… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic risks are present due to the ability of the bridge to alter total supply and individual balances. 7.5 Governance is centralized, as the admin can update metadata and administrative… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not implemented via proxy patterns in this contract. The contract is immutable in its logic, though administrative parameters like metadata can be updated. 7.8 Operations are… |

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


### `CP-01` — Privileged Minting Capability  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the bridge contract to increase the total supply of tokens at any time. This can dilute the value of existing holdings if not managed according to strict cross-chain protocols. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure the bridge contract is protected by robust multi-signature requirements to prevent unauthorized minting.


### `CP-02` — Privileged Balance Modification  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the bridge contract to remove tokens from any user's balance. This grants the bridge controller the power to effectively seize or destroy tokens from any address. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement strict off-chain monitoring and alerting for any crosschainBurn events to detect potential abuse of this privilege.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 68.4% of supply. What remains: 4.1% in wallets, 64.3% in other contracts. 511 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

511 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $594K (DexScreener, all pools). 24h trading volume $923K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $594K of DEX liquidity across 8 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6f18...fb07`](https://basescan.org/address/0x6f18277e5566090ad8ab35e401ce9155739bfb07) |
| **Network** | Base |
| **Price** | $0.00000875 |
| **24h Volume** | $920.2K |
| **Liquidity** | $590.5K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 2h |
| **Top-10 Holders** | 68.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2692 buys / 5328 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x66586da3aea24479b77183ef74dca95eb2b28541cb92f45d273e9790a4dd464a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/reboot-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
