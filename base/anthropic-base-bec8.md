---
token: Anthropic
ticker: ANTHROPIC
network: base
risk_score: 51
status: medium
date: 2026-10-29
---

# Anthropic (ANTHROPIC) — Smart Contract Security Analysis | Base

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anthropic-base-bec8)

---

## Audit Summary

ClankerToken is an ERC-20 compliant token with cross-chain capabilities integrated via the Superchain Token Bridge. The architecture relies on standard OpenZeppelin libraries for governance and voting, but includes privileged functions that allow for minting and burning of tokens. While these functions are restricted to the bridge address, they represent a significant centralization of control over the token supply.

> **Final Recommendation:** Users should be aware that the Superchain Token Bridge holds significant power over the token supply, including the ability to burn tokens from any address. We recommend that the protocol maintain transparency regarding the bridge's security posture and ensure that the admin keys are managed via a multi-signature wallet to mitigate single-point-of-failure risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin standards for ERC-20, Votes, and Permit functionality. 7.1 Architecture follows standard cross-chain patterns, while 7.2 Code Security is robust due to… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the bridge's authority to manipulate supply. While necessary for cross-chain functionality, the ability to burn tokens from any address creates a… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not implemented as the contract is not a proxy. 7.8 Operations are handled through standard administrative functions. The lack of upgradeability ensures immutability of the core… |

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


### `CP-01` — Centralized Minting Authority  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the bridge address to create new tokens at will, which can dilute the value of existing holdings. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement a hard cap on the total supply or introduce a timelock for significant minting events to protect token holders.


### `CP-02` — Bridge Authority to Burn User Tokens  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the bridge address to remove tokens directly from any user's balance, effectively allowing the bridge to seize or destroy user assets. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Restrict the burn functionality to only allow users to burn their own tokens, or implement a multi-step approval process for bridge-initiated burns.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 4,817 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,817 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.3M (DexScreener, all pools). 24h trading volume $63.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.3M of DEX liquidity across 1 pools. Launch: 365 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf216...f7c9`](https://basescan.org/address/0xf2166d39dd7e2712b81e96b4ab802764ef68f7c9) |
| **Network** | Base |
| **Price** | $0.000102 |
| **24h Volume** | $63.74M |
| **Liquidity** | $10.32M |
| **Volume / Liquidity** | 6.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1743 buys / 1606 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x1d726fbde08d8f8a9b8ceb35ce6702162c5711c9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anthropic-base-bec8)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
