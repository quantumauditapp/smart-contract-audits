---
token: Papertrade
ticker: PAPER
network: base
risk_score: 56
status: medium
date: 2026-10-18
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base-30f1)

---

## Audit Summary

The ClankerToken contract is an ERC-20 token with additional features for cross-chain operations and administrative control. While it implements standard ERC-20 functionality, it includes privileged functions that allow a designated `SuperchainTokenBridge` address to mint new tokens and burn tokens from any holder's balance. An `admin` role can also update administrative metadata. These centralized controls introduce significant economic and technical risks, particularly the ability to arbitrarily burn tokens from user accounts.

> **Final Recommendation:** To enhance the security and trustworthiness of the ClankerToken, it is critical to implement robust controls around the `SuperchainTokenBridge` address. This address currently holds significant power, including the ability to mint new tokens and arbitrarily burn tokens from any user's balance. We recommend securing this address with a multi-signature wallet requiring a high number of approvals, and establishing transparent, auditable operational procedures for all minting and burning actions.

Additionally, consider implementing time-locks for sensitive operations or introducing a community governance mechanism to oversee these powerful functions, thereby decentralizing control and reducing single points of failure. Regular security audits and continuous monitoring of the `SuperchainTokenBridge` address's activities are also advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The ClankerToken contract is an ERC-20 token that supports standard transfer, approval, and balance queries (7.1 Architecture). It includes extensions like ERC20Burnable, ERC20Votes, and ERC20Permit… |
| **Governance / Economics** | 1/10 | High | The economic model of ClankerToken is subject to significant centralized control (7.4 Economic). The `SuperchainTokenBridge` address has the power to mint new tokens via `crosschainMint`, which can… |
| **Upgrades** | 5/10 | Medium | The ClankerToken contract is not designed as an upgradeable proxy (7.7 Upgrades), as indicated by `is_proxy: false`. This means its logic cannot be modified after deployment. While this eliminates… |

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


### `CP-01` — Centralized Minting Capability  *(Severity: Informational · Status: Unresolved)*

The `crosschainMint` function allows a specific privileged address, `SuperchainTokenBridge`, to create new Clanker tokens and add them to any user's balance. This increases the total supply of tokens, which can dilute the value of existing token holdings. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure that the `SuperchainTokenBridge` address is controlled by a robust, multi-signature wallet or a decentralized governance mechanism. Implement strict operational procedures and monitoring for all minting operations.


### `CP-02` — Centralized Arbitrary Token Burning  *(Severity: Informational · Status: Unresolved)*

The `crosschainBurn` function enables the `SuperchainTokenBridge` address to remove any amount of Clanker tokens from any holder's balance without their consent. This poses a significant risk as it allows for arbitrary seizure or destruction of user assets. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Critically review the necessity of the `crosschainBurn` function's ability to burn tokens from arbitrary addresses. If essential for cross-chain functionality, ensure the `SuperchainTokenBridge` is secured by the highest standards, such as a multi-signature wallet with a high threshold, and that its operations are transparent and auditable. Consider implementing safeguards like time-locks or additional approvals for large burns.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 5,224 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,224 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.6M (DexScreener, all pools). 24h trading volume $55.5M (DexScreener, all pools).

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
| **Contract** | [`0x85f3...2b07`](https://basescan.org/address/0x85f316e96991e87b9ea960454723160f5ec92b07) |
| **Network** | Base |
| **Price** | $0.0001052 |
| **24h Volume** | $55.53M |
| **Liquidity** | $10.62M |
| **Volume / Liquidity** | 5.2× |
| **Token Age** | 21h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2986 buys / 2872 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xe2d1bd52c809e334304cd5283e0f247c7684836c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base-30f1)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-18*
