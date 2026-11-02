---
token: Anthropic
ticker: ANTHROPIC
network: base
risk_score: 54
status: medium
date: 2026-11-02
---

# Anthropic (ANTHROPIC) — Smart Contract Security Analysis | Base

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anthropic-base-1299)

---

## Audit Summary

The ClankerToken is an ERC-20 compliant token with cross-chain functionality integrated via the Superchain Token Bridge. The architecture relies on standard OpenZeppelin libraries for voting and permit functionality. While the core token logic is robust, the protocol grants significant power to the Superchain Token Bridge, which can mint or burn tokens at will. 7.1 Architecture: Standard ERC-20 with cross-chain extensions. 7.2 Code Security: High, utilizing audited OZ contracts. 7.3 Access Control: Centralized via Bridge. 7.4 Economic: Inflationary risk via minting. 7.5 Governance: Admin-controlled metadata. 7.6 External: Bridge dependency. 7.7 Upgrades: N/A. 7.8 Operations: Standard.

> **Final Recommendation:** Users should be aware that the Superchain Token Bridge holds absolute authority over the token supply and individual balances. Ensure that the bridge contract is monitored for any anomalous activity or unauthorized minting events. 

For the protocol team, consider implementing a timelock or multi-signature requirement for any administrative changes to the admin address. Regularly audit the bridge integration to ensure that cross-chain messaging remains secure and resistant to manipulation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-vetted OpenZeppelin standards for ERC-20, Votes, and Permit functionality. The code is clean and follows standard Solidity patterns for state management. However, the… |
| **Governance / Economics** | 1/10 | High | The token economic model is subject to inflationary pressure through the crosschainMint function. Token holders face dilution risk if the bridge is compromised or misconfigured. The admin role has… |
| **Upgrades** | 5/10 | Medium | The contract is not upgradeable and does not utilize proxy patterns. This ensures immutability of the core logic. Future changes would require a new contract deployment and migration, which is a safe… |

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

The crosschainMint function allows the Superchain Token Bridge to create new tokens at any time. This can lead to significant inflation and dilution of existing token holders' value. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement a hard cap on the total supply or require a multi-signature approval process for large minting operations.


### `CP-02` — Privileged Balance Manipulation  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the Superchain Token Bridge to remove tokens from any user's wallet. This grants the bridge controller the ability to seize assets or reduce user balances without user consent. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Restrict the burn functionality to only allow users to burn their own tokens, or implement a transparent, time-delayed process for any forced balance adjustments.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 5,022 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,022 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.2M (DexScreener, all pools). 24h trading volume $53.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.2M of DEX liquidity across 1 pools. Launch: 365 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfff1...cd55`](https://basescan.org/address/0xfff156d6fe2407fd000d396229c3868d2b01cd55) |
| **Network** | Base |
| **Price** | $0.000101 |
| **24h Volume** | $53.62M |
| **Liquidity** | $10.22M |
| **Volume / Liquidity** | 5.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1918 buys / 1860 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xca3d413878fec4ec2b2acd90c3db85e7f6c8e30a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anthropic-base-1299)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
