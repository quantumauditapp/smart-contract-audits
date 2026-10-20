---
token: Base
ticker: BASE
network: base
risk_score: 68
status: high
date: 2026-10-05
---

# Base (BASE) — Smart Contract Security Analysis | Base

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/base-base)

---

## Audit Summary

The ClankerToken contract implements an ERC-20 token with additional features for cross-chain operations and administrative control. While standard ERC-20 functionality is present, the contract includes privileged functions that allow an `admin` address to update metadata and, critically, a `SuperchainTokenBridge` address to mint and burn tokens arbitrarily. These privileged functions introduce significant centralization risks, as they can directly impact token supply and individual holder balances.

> **Final Recommendation:** It is crucial to ensure the `SuperchainTokenBridge` address is secured with the highest possible standards, ideally through a robust multi-signature wallet or a well-audited governance mechanism. Implement strict operational procedures and monitoring for all privileged actions, especially those involving `crosschainMint` and `crosschainBurn`. Consider implementing time-locks or additional governance checks for these critical functions to mitigate the impact of a single point of failure or compromise.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The ClankerToken contract is an ERC-20 compliant token with additional features for cross-chain transfers and administrative control (7.1 Architecture). It correctly implements standard ERC-20… |
| **Governance / Economics** | 3/10 | High | The economic model of the ClankerToken is highly dependent on the integrity and security of the `SuperchainTokenBridge` address (7.4 Economic). The `crosschainMint` function allows this privileged… |
| **Upgrades** | 6/10 | Medium | The ClankerToken contract is not implemented as an upgradeable proxy (7.7 Upgrades). This means its logic cannot be modified after deployment. While this eliminates upgrade-related risks such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 7 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xb4b8…5af6 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Centralized Token Minting Capability  *(Severity: Informational · Status: Unresolved)*

The `crosschainMint` function allows a specific address, `SuperchainTokenBridge`, to create new tokens and add them to any account's balance. This means the total supply of ClankerToken can be increased at will by this single entity. If this address is compromised or misused, it could lead to an uncontrolled increase in token supply, diluting the value for all existing token holders. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Token holders should be aware that the `SuperchainTokenBridge` address has the power to mint new tokens. It is recommended that the project ensures this address is controlled by a highly secure mechanism, such as a multi-signature wallet, and that any minting operations are transparently communicated and justified. Consider adding a time-lock or a community governance vote for significant minting events.


### `CP-02` — Centralized Arbitrary Token Burning Capability  *(Severity: Informational · Status: Unresolved)*

The `crosschainBurn` function grants the `SuperchainTokenBridge` address the ability to remove any amount of tokens from any holder's balance. This means the controlling entity can arbitrarily reduce or confiscate tokens from any user's wallet without their consent. This presents a severe centralization risk, as it gives a single entity direct control over individual token balances. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Token holders should understand that the `SuperchainTokenBridge` address can burn tokens from any account. It is critical for the project to secure this address with the highest level of protection, such as a multi-signature wallet with strong operational security. Transparency regarding all burn operations, along with clear policies and justifications, is essential to build and maintain trust. Consider implementing additional safeguards like time-locks or requiring multiple approvals for burni…


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 100.0% in wallets, 0.0% in other contracts. 2,538 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,538 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11.2M (DexScreener, all pools). 24h trading volume $48.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $11.2M of DEX liquidity across 6 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x728a...8b07`](https://basescan.org/address/0x728a536469cc655bddbca2b86098aa4e07168b07) |
| **Network** | Base |
| **Price** | $0.0001111 |
| **24h Volume** | $48.25M |
| **Liquidity** | $11.20M |
| **Volume / Liquidity** | 4.3× |
| **Token Age** | 21h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1319 buys / 807 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xa52d5bc6376258c94a40f4a36684ad73a77cfc57)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/base-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-05*
