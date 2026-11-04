---
token: AORP
ticker: AORP
network: base
risk_score: 69
status: high
date: 2026-11-04
---

# AORP (AORP) — Smart Contract Security Analysis | Base

> **Risk Score: 69/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aorp-base)

---

## Audit Summary

The ClankerToken is a standard ERC-20 implementation with cross-chain capabilities integrated via the Superchain Token Bridge. The architecture relies on the bridge contract to manage minting and burning operations. While the code follows standard OpenZeppelin patterns, the centralized control granted to the bridge contract introduces significant trust requirements for token holders.

> **Final Recommendation:** The protocol should ensure that the Superchain Token Bridge address is securely managed and that the bridge itself is subject to rigorous security audits. Users should be aware that the bridge holds the power to modify balances and total supply.

Regular monitoring of the bridge's cross-chain transactions is recommended to detect any anomalous minting or burning activity. No further code changes are required for the current implementation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes robust OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is well-structured for cross-chain compatibility. 7.2 Code Security is high due to… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the bridge's authority. The ability to mint and burn tokens allows for supply manipulation and direct balance modification. While necessary for… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not implemented via proxy patterns in this contract. The contract is immutable in its current deployment. 7.8 Operations are limited to administrative metadata updates, which are… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 96.7% of supply. What remains: 28.1% in wallets, 68.6% in other contracts. The deployer/owner wallet itself holds 21.8%. A holder that also controls the contract can sell into its own liquidity. 1,031 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Privileged Minting Authority  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the Superchain Token Bridge to increase the total supply of tokens at any time. This can lead to the dilution of existing token holders' value if the bridge is compromised or misconfigured. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure the bridge contract is secured with multi-signature requirements and strictly audited logic to prevent unauthorized minting.


### `CP-02` — Privileged Balance Modification  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the Superchain Token Bridge to directly remove tokens from any user's balance. This grants the bridge controller the ability to seize or destroy tokens held by any address. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement strict circuit breakers or rate limits on the bridge's ability to burn tokens to mitigate the impact of a potential bridge compromise.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,031 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $289K (DexScreener, all pools). 24h trading volume $51K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $289K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcdb4...2078`](https://basescan.org/address/0xcdb4f0511e6d4709ca18a6d2632242de7ac32078) |
| **Network** | Base |
| **Price** | $0.00000349 |
| **24h Volume** | $51.4K |
| **Liquidity** | $289.1K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 4h |
| **Top-10 Holders** | 96.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2546 buys / 538 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x7d1d58dd46607f754a7874c5daa6ba18ffa38e72f018d02e1621defcc857d8dd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aorp-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
