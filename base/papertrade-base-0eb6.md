---
token: Papertrade
ticker: PAPER
network: base
risk_score: 58
status: medium
date: 2026-10-20
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base-0eb6)

---

## Audit Summary

The ClankerToken is an ERC-20 compliant token with cross-chain capabilities integrated via the Superchain Token Bridge. The architecture relies on the bridge contract to manage supply fluctuations. While the implementation follows standard OpenZeppelin patterns, the centralized control granted to the bridge contract introduces significant trust requirements for token holders.

> **Final Recommendation:** Token holders should be aware that the Superchain Token Bridge holds the authority to mint and burn tokens, which is a necessary feature for cross-chain interoperability but represents a central point of trust. Ensure that the bridge contract address is verified and monitored for any anomalous activity.

Maintain strict security over the admin address, as it controls metadata and administrative roles. Consider implementing a multi-signature wallet or a timelock for the admin role to mitigate the risk of unauthorized configuration changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes robust OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, leveraging standard cross-chain interfaces. 7.2 Code Security is high due… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risk is tied to the bridge's ability to mint and burn tokens, which directly impacts supply. 7.5 Governance is centralized under an admin address capable of updating metadata and… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not implemented via proxy patterns in this contract. 7.8 Operations are stable as the contract is immutable regarding its core logic. No upgrade paths exist for the token contract… |

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


### `CP-01` — Centralized Minting Authority  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the Superchain Token Bridge to create new tokens at will. This increases the total supply and can dilute the value of existing holdings. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure the bridge contract is secured by a multi-signature wallet and that minting events are monitored by an automated alerting system.


### `CP-02` — Centralized Burn Authority  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the Superchain Token Bridge to remove tokens from any user's balance. This effectively gives the bridge the power to seize or destroy user assets. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement strict access controls and transparency logs for all cross-chain burn operations to ensure they are only triggered by legitimate user-initiated bridge requests.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 4,816 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,816 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.3M (DexScreener, all pools). 24h trading volume $44.0M (DexScreener, all pools).

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
| **Contract** | [`0x6aed...4b07`](https://basescan.org/address/0x6aedabf7d4e0302d776fbf8eb11cfb1993764b07) |
| **Network** | Base |
| **Price** | $0.000102 |
| **24h Volume** | $44.04M |
| **Liquidity** | $10.30M |
| **Volume / Liquidity** | 4.3× |
| **Token Age** | 11h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2577 buys / 2422 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x04293f1c73efaedbcc2b1c209f2f0a053cc35884)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base-0eb6)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
