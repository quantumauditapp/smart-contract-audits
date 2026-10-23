---
token: Noerra
ticker: NOERRA
network: ethereum
risk_score: 33
status: low
date: 2026-10-23
---

# Noerra (NOERRA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/noerra-eth)

---

## Audit Summary

NoerraRevenueCoin is a standard ERC-20 token implementing a custom launch protection mechanism. The architecture relies on a centralized launch authority to configure market parameters, ensuring the token is paired with a verified market contract. The code is well-structured and follows standard OpenZeppelin patterns for ERC-20 functionality. Coverage: 7.1 Architecture (Standard), 7.2 Code Security (High), 7.3 Access Control (Centralized), 7.4 Economic (Launch-gated), 7.5 Governance (N/A), 7.6 External (Market-dependent), 7.7 Upgrades (None), 7.8 Operations (Standard).

> **Final Recommendation:** The protocol is secure for standard ERC-20 operations. Users should monitor the `launchMarket` address to understand the specific transfer restrictions enforced during the protection window, as these are determined by external contract logic.

We recommend that the `launchAuthority` address be transitioned to a multi-signature wallet or a time-locked contract if the project intends to maintain long-term control over market configurations, reducing the risk of a single private key compromise.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a robust ERC-20 implementation with clear separation of concerns. The logic for launch protection is strictly gated by block numbers and market verification, preventing… |
| **Governance / Economics** | 2/10 | High | The economic model is heavily centralized during the launch phase, granting significant control to the `launchAuthority` and `launchMarket`. While this prevents malicious liquidity setups, it creates… |
| **Upgrades** | 6/10 | Medium | The contract is immutable and does not utilize proxy patterns. There are no upgrade mechanisms, which eliminates risks associated with logic changes or malicious proxy updates. The current state is… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x0dad…d24e — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-08` — Centralized Control Over Transfer Restrictions  *(Severity: Low · Status: Unresolved)*

The `beginLaunchProtection` function allows the `launchMarket` address to define the duration of transfer restrictions. This gives the controller of the launch market the ability to influence token liquidity and transferability during the initial launch phase.

**Recommendation:** Ensure that the `launchMarket` contract is audited and that its logic for managing transfer restrictions is transparent to the community. Consider implementing a maximum cap on the protection duration to prevent indefinite locking of tokens.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 43.1% of supply. What remains: 15.8% in wallets, 27.3% in other contracts. 80 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

80 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $56K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: launchmarket — a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2b91...bc6b`](https://etherscan.io/address/0x2b91b31c087ed6cde9b63fd0c59e4bbc611fbc6b) |
| **Network** | Ethereum |
| **Price** | $0.00002105 |
| **24h Volume** | $56.4K |
| **Liquidity** | $11.9K |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 12h |
| **Top-10 Holders** | 43.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 220 buys / 116 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x8203ae75df335b0907e6f333dbe43d50fd5016f3c47283face74303d0cb83e8c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/noerra-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
