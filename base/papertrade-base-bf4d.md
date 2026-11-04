---
token: Papertrade
ticker: PAPER
network: base
risk_score: 52
status: medium
date: 2026-11-04
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 52/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base-bf4d)

---

## Audit Summary

The ClankerToken is an ERC-20 compliant token on the Base network designed for cross-chain interoperability via the Superchain Token Bridge. The architecture relies on standard OpenZeppelin libraries for voting and permit functionality. While the core token logic is robust, the protocol grants significant power to the Superchain Token Bridge to mint and burn tokens, which introduces centralized risks to token supply and holder balances.

> **Final Recommendation:** Token holders should be aware that the Superchain Token Bridge holds the authority to mint and burn tokens, which is a necessary feature for cross-chain functionality but represents a centralized point of failure. We recommend monitoring the bridge's security posture and governance updates closely.

For future iterations, consider implementing a multi-signature or timelock mechanism for administrative functions like updateAdmin to prevent unauthorized changes to contract metadata or administrative roles.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin standards for ERC-20, Votes, and Permit functionality. 7.1 Architecture follows standard cross-chain patterns, while 7.2 Code Security is high due to… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the bridge's authority. The ability to mint and burn tokens allows for potential supply manipulation if the bridge contract is compromised. While… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not implemented in this contract, as it is a standard non-proxy deployment. 7.8 Operations are straightforward, with administrative functions limited to metadata updates. The lack of… |

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


### `CP-01` — Privileged Minting Authority  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the Superchain Token Bridge to create new tokens at will. This increases the total supply and dilutes the value of existing holdings. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure that the bridge contract is secured by a robust multi-signature wallet or decentralized governance to prevent unauthorized minting.


### `CP-02` — Privileged Balance Modification  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the Superchain Token Bridge to remove tokens from any user's balance. This effectively grants the bridge the power to seize or destroy user assets. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement strict circuit breakers or monitoring tools to detect and alert on large-scale burn operations that could indicate a bridge compromise.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 5,305 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,305 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.3M (DexScreener, all pools). 24h trading volume $54.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.3M of DEX liquidity across 1 pools. Launch: 365 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3954...6b2a`](https://basescan.org/address/0x3954784974ebbdba40805dc7723fb2c45ea66b2a) |
| **Network** | Base |
| **Price** | $0.000102 |
| **24h Volume** | $54.38M |
| **Liquidity** | $10.32M |
| **Volume / Liquidity** | 5.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2607 buys / 2416 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x40b29d46cf2498d862d5bae174c18678ebe42c0b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base-bf4d)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
