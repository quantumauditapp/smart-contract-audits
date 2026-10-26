---
token: Papertrade
ticker: PAPER
network: base
risk_score: 80
status: high
date: 2026-10-26
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 80/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base-59d0)

---

## Audit Summary

The ClankerToken is a standard ERC-20 implementation with cross-chain capabilities via the Superchain Token Bridge. The architecture relies on the bridge contract to manage supply across chains, which introduces centralized control points. While the code follows standard OpenZeppelin patterns, the ability for the bridge to burn and mint tokens creates significant trust requirements for users.

> **Final Recommendation:** Users should be aware that the Superchain Token Bridge holds the authority to mint and burn tokens, which is a necessary feature for cross-chain interoperability but represents a centralized risk. Ensure that the bridge contract is monitored for any unauthorized activity or security incidents.

Maintain strict security over the admin address, as it controls metadata and the admin role itself. Consider implementing a multi-signature wallet for the admin role to prevent single-point-of-failure risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes robust, battle-tested libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, separating cross-chain logic from standard token operations. 7.2 Code… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risks are present due to the minting and burning capabilities of the bridge. 7.5 Governance is centralized under an admin role for metadata updates. 7.6 External dependencies are limited… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not implemented via proxy patterns in this contract. 7.8 Operations are straightforward, with admin functions limited to metadata and admin address updates. No complex upgrade logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 5 Informational_

### `CP-02` — Privileged Balance Manipulation  *(Severity: High · Status: Unresolved)*

The crosschainBurn function allows the Superchain Token Bridge to remove tokens directly from any user's balance. This grants the bridge the power to effectively seize or destroy user assets.

**Recommendation:** Implement strict monitoring and circuit breakers on the bridge contract to prevent unauthorized or malicious burning of user tokens.


### `CP-01` — Privileged Minting Capability  *(Severity: Medium · Status: Unresolved)*

The crosschainMint function allows the Superchain Token Bridge to increase the total supply of tokens. This action dilutes the holdings of all existing token holders.

**Recommendation:** Ensure the bridge contract is secure and that the minting process is transparently logged and audited.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x63e5…4cb6 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 6,604 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

6,604 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.2M (DexScreener, all pools). 24h trading volume $33.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner key. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.2M of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2793...1b07`](https://basescan.org/address/0x279326616f0bbf9c2c47c50febab5da469681b07) |
| **Network** | Base |
| **Price** | $0.000101 |
| **24h Volume** | $33.64M |
| **Liquidity** | $10.21M |
| **Volume / Liquidity** | 3.3× |
| **Token Age** | 2h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1539 buys / 1397 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xf5e4214e176fe626696d65ed39a553c1a1063687)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base-59d0)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
