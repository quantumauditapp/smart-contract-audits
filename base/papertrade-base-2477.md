---
token: Papertrade
ticker: PAPER
network: base
risk_score: 52
status: medium
date: 2026-10-30
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 52/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base-2477)

---

## Audit Summary

The ClankerToken is an ERC-20 compliant token with cross-chain capabilities via the Superchain Token Bridge. The architecture relies on standard OpenZeppelin libraries for voting and permit functionality. While the core token logic is robust, the protocol grants significant power to the Superchain Token Bridge to mint and burn tokens, which introduces centralized control risks.

> **Final Recommendation:** The protocol should implement a multi-signature wallet or a time-lock mechanism for the admin address to mitigate the risk of unauthorized metadata or administrative changes. Additionally, ensure that the Superchain Token Bridge address is monitored for any anomalous activity, as it holds the authority to alter token balances.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard ERC-20, ERC-20Votes, and ERC-20Permit interfaces, ensuring high compatibility with DeFi ecosystems. 7.1 Architecture is modular, utilizing established OpenZeppelin… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risks are present due to the ability of the bridge to mint and burn tokens, which directly impacts supply and holder balances. 7.5 Governance is centralized under an admin role capable… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not explicitly supported via proxy patterns in this implementation. The contract is immutable, which eliminates risks associated with malicious logic updates. 7.8 Operations are… |

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

The crosschainMint function allows the Superchain Token Bridge to create new tokens at will. This increases the total supply and dilutes the value held by existing token holders. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement a hard cap on the total supply or require a governance vote for significant minting events to protect token holders from unexpected dilution.


### `CP-02` — Privileged Balance Manipulation  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the Superchain Token Bridge to remove tokens from any user's balance. This grants the bridge controller the power to effectively seize or destroy user assets. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Restrict the burn functionality to only allow users to burn their own tokens, or implement a multi-step verification process for cross-chain burns to prevent unauthorized asset removal.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 5,210 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,210 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.3M (DexScreener, all pools). 24h trading volume $39.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.3M of DEX liquidity across 1 pools. Launch: 365 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4f24...0402`](https://basescan.org/address/0x4f2488db97e4dc764c2fccbf03e088e48de40402) |
| **Network** | Base |
| **Price** | $0.000102 |
| **24h Volume** | $39.76M |
| **Liquidity** | $10.32M |
| **Volume / Liquidity** | 3.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1485 buys / 1359 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xaa41f85e50a5b53889f01546d6c751ea9b7336a1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base-2477)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
