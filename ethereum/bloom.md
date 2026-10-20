---
token: Bloom
ticker: BLOOM
network: ethereum
risk_score: 69
status: high
date: 2026-10-20
---

# Bloom (BLOOM) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 69/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bloom-eth)

---

## Audit Summary

The Token contract implements a specialized launch mechanism with external hook-based logic. The architecture relies on a central 'pollenHook' to manage state and fund distribution. While the core ERC-20 functionality is standard, the custom logic for fund gathering and distribution introduces centralized control points that require trust in the designated hook and keeper addresses.

> **Final Recommendation:** The protocol is well-implemented with clear access control boundaries. Ensure that the address assigned to the bindingAuthority and the subsequent pollenHook are managed by secure, multi-signature wallets to mitigate the risk of centralized control abuse.

Monitor the interaction with external BloomBinding contracts closely, as the security of the reserve distribution depends entirely on the integrity of the hooked contract's logic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes OpenZeppelin's ReentrancyGuard to protect state-changing functions like gather(). 7.1 Architecture: The design uses a modular hook system to delegate complex logic. 7.2 Code… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: The contract manages internal reserves via scatter and reserveKeeper functions. 7.5 Governance: The bindingAuthority controls the initial hook setup, which is a centralized point of… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades: The contract is not upgradeable. 7.8 Operations: The operational lifecycle is defined by the start() function, which sets the initial timestamp. No further administrative changes to the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xae4d…ca90 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-08` — Centralized Control Over Launch Timing  *(Severity: Low · Status: Unresolved)*

The start() function allows the initializer to set the contract's start time, which effectively controls when transfer rules become active. This is a one-time configuration that dictates the lifecycle of the token launch.

**Recommendation:** Ensure the initializer address is a secure, time-locked, or multi-signature account to prevent unauthorized or premature activation of the token launch.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 0.1% burned — not holders that can sell, so excluded from the concentration score. What remains: 0.9% in wallets, 99.0% in other contracts. 7 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

7 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $16K (DexScreener, all pools). 24h trading volume $37K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $16K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0c7f...e833`](https://etherscan.io/address/0x0c7f2155c40a11154b760f784f50e253809ae833) |
| **Network** | Ethereum |
| **Price** | $0.1614 |
| **24h Volume** | $36.9K |
| **Liquidity** | $16.1K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 4h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 218 buys / 86 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x32270eb2d759b7024b186fb8cff5753e86ec14e224c4a5e74483118e6e6b5945)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bloom-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
