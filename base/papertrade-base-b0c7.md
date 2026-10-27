---
token: Papertrade
ticker: PAPER
network: base
risk_score: 54
status: medium
date: 2026-10-27
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base-b0c7)

---

## Audit Summary

ClankerToken is an ERC-20 compliant token on the Base network, designed to support cross-chain functionality via the Superchain Token Bridge. The contract implements standard voting and permit features. While the core logic is robust, the protocol grants significant power to a specific bridge address to mint and burn tokens, which introduces centralized risk.

> **Final Recommendation:** The protocol should ensure that the Superchain Token Bridge address is monitored for any anomalous activity. Given the high-privilege nature of the bridge, implementing a multi-signature or timelock mechanism for administrative updates to the bridge configuration would enhance security.

Users should be aware that the token supply is dynamic and controlled by the bridge. Regular audits of the bridge contract itself are recommended to ensure that the cross-chain minting and burning logic remains secure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows standard OpenZeppelin patterns for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, 7.2 Code Security is high due to standard library usage, and 7.3… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the bridge's authority. The ability to mint and burn tokens directly affects the total supply and individual holder balances. While necessary for… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not currently implemented as the contract is not a proxy. 7.8 Operations are straightforward, relying on the immutability of the deployed bytecode. No upgrade paths exist for the… |

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

The crosschainMint function allows the Superchain Token Bridge to create new tokens at will. This increases the total supply and dilutes the value of existing holdings. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure the bridge contract is secured and audited, as it holds the power to inflate the token supply.


### `CP-02` — Direct Balance Manipulation via Bridge  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the Superchain Token Bridge to remove tokens from any user's balance. This grants the bridge the ability to force-burn tokens from any address. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Restrict the bridge's ability to burn tokens to only those explicitly approved or initiated by the token holder, if possible.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 5,011 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,011 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.6M (DexScreener, all pools). 24h trading volume $34.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.6M of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf595...9b07`](https://basescan.org/address/0xf5954f33798529917c4940317cada852f00c9b07) |
| **Network** | Base |
| **Price** | $0.0001052 |
| **24h Volume** | $34.54M |
| **Liquidity** | $10.63M |
| **Volume / Liquidity** | 3.2× |
| **Token Age** | 7h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2055 buys / 1911 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xbaa1b5744f9c6662e876997545294a9e9bdc04f3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base-b0c7)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
