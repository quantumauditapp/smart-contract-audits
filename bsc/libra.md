---
token: Libra
ticker: LIBRA
network: bsc
risk_score: 45
status: medium
date: 2026-09-30
---

# Libra (LIBRA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/libra-bsc)

---

## Audit Summary

The Token contract is an ERC-20 standard token. Its ownership has been renounced on-chain, meaning no single entity can currently control privileged functions. A mechanism to control transfer rules (`setMode`) exists but is now dormant due to renounced ownership. The audit identified one informational finding related to this dormant control, indicating a very low overall risk profile.

> **Final Recommendation:** Token holders should be aware that the contract's ownership has been renounced, making all owner-restricted functions permanently inactive. This ensures that no single entity can alter the token's core behavior, such as transfer rules. While this enhances decentralization and reduces certain risks, it also means that any potential issues or desired feature changes cannot be implemented. Users should verify the current state of the `_mode` variable to understand the active transfer rules, as it cannot be changed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Token contract implements standard ERC-20 functionality, including `transfer`, `transferFrom`, `balanceOf`, and `totalSupply`. The core transfer logic appears sound (7.2 Code Security). A `_mode`… |
| **Governance / Economics** | 8/10 | Low | The contract includes a `setMode` function that could alter transfer rules by changing the `_mode` state variable (7.4 Economic). This function was originally restricted to the contract owner.… |
| **Upgrades** | 8/10 | Low | The Token contract is not implemented as a proxy and does not include any upgradeability mechanisms (7.7 Upgrades). This means the contract's logic is immutable and cannot be changed post-deployment.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 89.8% |
| **LP Locked** | 89.8% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity only partly locked or burned  *(Severity: Medium · Status: Acknowledged)*

89.8% of the pool's LP is burned or time-locked. 89.8% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 3.2% is held, unlocked, by 9 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-05` — A privileged address controls a switch that decides whether transfers go through  *(Severity: Informational · Status: Unresolved)*

An on/off setting checked in the transfer path can be changed by a privileged function; depending on its value, transfers or sales are allowed or refused. Ownership is renounced, so no one can call these functions now. Functions: setMode. Restricted to: owner.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 79.4% of supply. Of that, 9.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.2% in wallets, 70.0% in other contracts. 146,992 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

146,992 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.2M (DexScreener, all pools). 24h trading volume $199K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on four.meme, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.2M of DEX liquidity across 3 pools. Launch: launched on four.meme, 342 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd28e...4444`](https://bscscan.com/address/0xd28e716fa02543962b3129f9e4d919c65f434444) |
| **Network** | BNB Chain |
| **Price** | $0.006812 |
| **24h Volume** | $198.7K |
| **Liquidity** | $1.23M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 79.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5885 buys / 5990 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x5166508edf57c5218b0755acefd0fe25f253c084)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/libra-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-30*
