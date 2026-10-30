---
token: Swarm
ticker: SWARM
network: bsc
risk_score: 76
status: high
date: 2026-10-30
---

# Swarm (SWARM) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 76/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/swarm-bsc)

---

## Audit Summary

SwarmToken is an ERC-20 token contract deployed on BSC. While ownership has been renounced, the contract retains a 'minter' role that holds significant power over token supply and trading functionality. The architecture is standard, but the centralization of control via the minter role introduces economic risks for token holders.

> **Final Recommendation:** Token holders should be aware that the 'minter' address possesses the ability to dilute the supply and toggle trading states. It is recommended that the project team eventually renounce the minter role or transition it to a multi-signature wallet or a time-locked governance contract to mitigate centralization risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements standard ERC-20 functionality using OpenZeppelin-like patterns. 7.1 Architecture is straightforward, utilizing a single-contract design. 7.2 Code Security is high, with no… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance aspects are dominated by the minter role. The minter can arbitrarily increase supply up to a hard cap, directly impacting token value. 7.6 External dependencies are… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are stable due to the immutable nature of the contract logic. No upgrade risk exists for this implementation. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 2 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The 'minter' address has the authority to call the mint() function, which creates new tokens and increases the total supply. This allows the controller to dilute the holdings of existing token holders at any time.

**Recommendation:** Consider renouncing the minter role or implementing a time-lock mechanism to ensure that any future minting events are transparent and subject to community oversight.


### `CP-05` — Trading Control Switch  *(Severity: Medium · Status: Unresolved)*

The 'minter' address controls the openTrading() function, which acts as a master switch for token transfers. By controlling this, the minter can effectively halt all trading activity for the token, preventing users from moving or selling their assets.

**Recommendation:** Restrict the ability to toggle trading states to a decentralized governance process rather than a single privileged address.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 47.9% of supply. Of that, 35.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 13.0% in wallets, 0.0% in other contracts. 1,114 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,114 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $25K (DexScreener, all pools). 24h trading volume $632K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 2% on sell. Market: $25K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x04fd...4afa`](https://bscscan.com/address/0x04fd77c2f97d044b3c719282fd0a0568f4254afa) |
| **Network** | BNB Chain |
| **Price** | $0.00000004 |
| **24h Volume** | $631.6K |
| **Liquidity** | $24.6K |
| **Volume / Liquidity** | 25.7× |
| **Token Age** | 11h |
| **Top-10 Holders** | 47.9% of supply |
| **Buy / Sell Tax** | 1.0% / 2.0% |
| **24h Transactions** | 6367 buys / 5386 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x933bfba8d4f91825d137f72cb9914584b16967e2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/swarm-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
