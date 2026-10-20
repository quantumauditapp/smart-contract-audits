---
token: Papertrade
ticker: PAPER
network: base
risk_score: 54
status: medium
date: 2026-10-15
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base-d72e)

---

## Audit Summary

The ClankerToken contract is an ERC-20 token with additional features for burning, voting, and cross-chain operations. The audit identified significant centralization risks related to token supply management and balance manipulation. A privileged `SuperchainTokenBridge` address has the ability to mint new tokens and burn tokens from any holder's account, posing a high risk to token holders.

> **Final Recommendation:** Token holders should be fully aware of the extensive control held by the `SuperchainTokenBridge` address, which can mint new tokens and burn existing tokens from any account. It is crucial to understand the identity and security practices of the entity controlling this address. For enhanced security and decentralization, consider implementing a multi-signature wallet or a time-locked contract for the `SuperchainTokenBridge` role, and explore mechanisms to gradually decentralize these powerful functions over time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The ClankerToken contract implements standard ERC-20 functionalities, including burnable, voting, and permit extensions. The architecture includes an `_admin` role for administrative tasks like… |
| **Governance / Economics** | 1/10 | High | The contract incorporates ERC-20 voting mechanisms, allowing token holders to participate in governance if an external system utilizes these votes (7.5 Governance). However, the economic model is… |
| **Upgrades** | 5/10 | Medium | The ClankerToken contract is not designed with an upgrade mechanism, meaning its logic cannot be modified after deployment (7.7 Upgrades). This eliminates risks associated with proxy patterns… |

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


### `CP-01` — Centralized Token Minting Capability  *(Severity: Informational · Status: Unresolved)*

The `crosschainMint` function allows a specific privileged address, `SuperchainTokenBridge`, to create new tokens at will. This means that the total supply of ClankerToken can be increased without limit, potentially diluting the value of existing tokens held by users. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Token holders should be aware that the `SuperchainTokenBridge` can increase the token supply. To mitigate this risk, consider implementing a multi-signature wallet for the `SuperchainTokenBridge` address or a time-lock mechanism for minting operations, providing transparency and requiring multiple approvals.


### `CP-02` — Centralized Token Burning Capability from Any Account  *(Severity: Informational · Status: Unresolved)*

The `crosschainBurn` function grants the `SuperchainTokenBridge` address the power to burn (destroy) tokens from *any* holder's account. This means that the controller of `SuperchainTokenBridge` can arbitrarily reduce or zero out any user's ClankerToken balance, leading to a direct loss of funds for token holders. Ownership is renounced, so no one can call these functions now.

**Recommendation:** This is a critical centralization point. Token holders must understand that the `SuperchainTokenBridge` can remove tokens from their wallets. It is strongly recommended to secure the `SuperchainTokenBridge` address with a robust multi-signature setup and to establish clear, transparent policies for when and why such burns would occur, if ever.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 5,013 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,013 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.2M (DexScreener, all pools). 24h trading volume $54.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.2M of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x503f...8b07`](https://basescan.org/address/0x503fdcc939ed5c10acfb495209fa9d36c5988b07) |
| **Network** | Base |
| **Price** | $0.000101 |
| **24h Volume** | $54.68M |
| **Liquidity** | $10.20M |
| **Volume / Liquidity** | 5.4× |
| **Token Age** | 3h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1281 buys / 1138 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xe01949e8518eca971ca0e7451ee4ca8c67dbdcff)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base-d72e)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
