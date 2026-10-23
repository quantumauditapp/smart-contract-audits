---
token: Quickdraw
ticker: DRAW
network: ethereum
risk_score: 78
status: high
date: 2026-10-23
---

# Quickdraw (DRAW) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 78/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/quickdraw-eth)

---

## Audit Summary

The QuickdrawToken contract implements a custom ERC-20 token with tight integration to an external game contract. While the core transfer logic follows standard patterns, the protocol grants the game contract excessive authority over user balances. 7.1 Architecture: Centralized control via a game contract. 7.2 Code Security: Standard ERC-20 implementation with custom hooks. 7.3 Access Control: High centralization risk. 7.4 Economic: Fee manipulation possible. 7.5 Governance: Initializer-based setup. 7.6 External: Heavy dependency on game contract. 7.7 Upgrades: Not applicable. 7.8 Operations: Standard.

> **Final Recommendation:** Users should be aware that the game contract holds absolute authority over their token balances, including the ability to move or burn tokens without user consent. It is recommended to verify the source code and security audits of the bound game contract before interacting with the token.

For future iterations, consider implementing a more decentralized governance model or limiting the game contract's ability to modify balances to specific, audited scenarios to reduce the trust requirement on the game contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes standard ERC-20 logic with integrated hooks for game-specific state updates. The code is clean and follows modern Solidity practices, including the use of custom errors.… |
| **Governance / Economics** | 1/10 | High | The economic model is entirely dependent on the game contract's behavior. The initializer has the power to start the token lifecycle, while the game contract acts as a central authority over all user… |
| **Upgrades** | 6/10 | Medium | The contract does not implement proxy patterns or upgradeability features. The logic is immutable once deployed. This eliminates upgrade-related risks but prevents patching if vulnerabilities are… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 5 Informational_

### `CP-02` — Centralized Control Over User Balances  *(Severity: High · Status: Unresolved)*

The game contract has the authority to call gameMove and gameBurn, which allow it to arbitrarily move tokens between addresses or burn tokens from any user's wallet. This effectively removes the concept of user ownership, as the game contract can unilaterally reduce or redistribute any user's balance.

**Recommendation:** Restrict the game contract's ability to modify balances to only specific, user-initiated actions or implement a multi-signature requirement for balance adjustments.


### `CP-07` — Centralized Fee Configuration  *(Severity: Medium · Status: Unresolved)*

The initializer address has the power to set the initial state, which influences the transfer fee structure. This allows the initializer to potentially change the economic parameters of the token at the start of the protocol's lifecycle.

**Recommendation:** Consider using a decentralized governance mechanism or a time-locked contract to manage fee changes rather than a single initializer address.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xa6f3…e168 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.8% of supply. What remains: 5.2% in wallets, 94.6% in other contracts. 22 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

22 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $21K (DexScreener, all pools). 24h trading volume $59K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $21K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xeb1a...83a3`](https://etherscan.io/address/0xeb1ad60a119a5d239122844e6f64ae1c5fb483a3) |
| **Network** | Ethereum |
| **Price** | $0.2118 |
| **24h Volume** | $58.5K |
| **Liquidity** | $20.8K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 5h |
| **Top-10 Holders** | 99.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 244 buys / 190 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x969437174469f37d71f5101ae5c04ab3b2418c484ffbce38a325bef08477df07)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/quickdraw-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
