---
token: Papertrade
ticker: PAPER
network: base
risk_score: 68
status: high
date: 2026-10-14
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base-f58d)

---

## Audit Summary

The ClankerToken contract is an ERC-20 token implementation with additional features for cross-chain operations and administrative control. The audit identified significant centralized control points, specifically the ability for a privileged address to mint new tokens and directly burn tokens from any holder's balance. These capabilities introduce high technical and economic risks.

> **Final Recommendation:** It is crucial to implement robust security measures for the `SuperchainTokenBridge` address, as it holds significant power over the token supply and individual balances. Consider implementing multi-signature control or a time-locked governance mechanism for these critical functions to mitigate the risk of a single point of failure or compromise. Additionally, ensure transparent communication with token holders regarding the capabilities of privileged addresses and the intended use of cross-chain minting and burning functionalities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The ClankerToken contract implements the ERC-20 standard, including burnable, votes, and permit functionalities. The contract includes several privileged functions: `updateAdmin`, `updateImage`, and… |
| **Governance / Economics** | 1/10 | High | The economic model of ClankerToken is highly centralized due to the `SuperchainTokenBridge`'s ability to mint and burn tokens. The `crosschainMint` function allows this address to increase the total… |
| **Upgrades** | 2/10 | High | The ClankerToken contract is not designed as an upgradeable proxy. It is a standard implementation contract, meaning its logic cannot be changed after deployment. This design choice eliminates… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 5 Informational_

### `CP-02` — A privileged address can directly change any holder's token balance  *(Severity: High · Status: Unresolved)*

The `crosschainBurn` function allows the `SuperchainTokenBridge` address to burn tokens from any account. This means the privileged address can arbitrarily reduce or zero out any token holder's balance without their consent, effectively confiscating their tokens.

**Recommendation:** The `SuperchainTokenBridge` address must be protected with the most stringent security protocols, ideally a multi-signature wallet with a high threshold of signers. Implement comprehensive monitoring and alerting for all `crosschainBurn` operations. Clearly communicate the intended use and limitations of this power to the community, and consider if such a direct balance manipulation capability is strictly necessary or if alternative, less centralized mechanisms could be used.


### `CP-01` — A privileged address can create new tokens, diluting existing holders  *(Severity: Medium · Status: Unresolved)*

The `crosschainMint` function allows the `SuperchainTokenBridge` address to mint any amount of new ClankerToken. This capability means that a single privileged entity can increase the total supply of tokens at will, which directly dilutes the value of tokens held by all other token holders.

**Recommendation:** Ensure that the `SuperchainTokenBridge` address is secured with the highest possible standards, such as a robust multi-signature wallet. Implement strict operational policies and monitoring for all minting activities. Consider adding a rate limit or a time-lock for large minting operations, or requiring a governance vote for significant supply increases.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 4,811 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,811 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.2M (DexScreener, all pools). 24h trading volume $61.7M (DexScreener, all pools).

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
| **Contract** | [`0xc54a...0b07`](https://basescan.org/address/0xc54a9e149d964a8e8620f685be8a09e0acbf0b07) |
| **Network** | Base |
| **Price** | $0.000101 |
| **24h Volume** | $61.69M |
| **Liquidity** | $10.20M |
| **Volume / Liquidity** | 6.0× |
| **Token Age** | 7h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1598 buys / 1466 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x434794da8b2f897287a32259c818612a2acc5c0b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base-f58d)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-14*
