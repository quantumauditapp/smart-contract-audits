---
token: Un1corn
ticker: UN1
network: ethereum
risk_score: 84
status: high
date: 2026-10-21
---

# Un1corn (UN1) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/un1corn-eth)

---

## Audit Summary

The UN1Token protocol implements a complex token system with integrated NFT-like card mechanics and reward distribution. The architecture relies heavily on privileged roles (deployer, mirror, beacon, distributor) that possess significant control over token supply, transfer logic, and external contract dependencies. While the code structure is modular, the high degree of centralization and the presence of uninitialized state variables pose significant risks to system integrity.

> **Final Recommendation:** Immediate remediation of uninitialized state variables and the implementation of a secure, verifiable source of randomness are required. We recommend transitioning from centralized privileged roles to a multi-signature wallet or a decentralized governance contract to mitigate the risk of single-point-of-failure exploits.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 2/10 | High | The architecture utilizes a multi-role system to manage token lifecycle and reward distribution. 7.1 Architecture: Highly modular but complex, relying on external hooks and beacons. 7.2 Code… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: Token supply is dynamic and controlled by privileged roles, creating potential for dilution. 7.5 Governance: No decentralized governance is present; all parameters are managed by… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades: The protocol lacks a formal proxy pattern but allows for the replacement of critical external dependencies via the initialize function. 7.8 Operations: Operational security is entirely… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 3 High · 🟡 3 Medium · 🟢 2 Low · ⚪ 5 Informational_

### `CD-02` — Uninitialized State Variables  *(Severity: High · Status: Unresolved)*

Variables related to card management are used before being initialized, which can lead to undefined behavior or system failure.

**Recommendation:** Ensure all state variables are explicitly initialized in the constructor or the initialize function.


### `CD-03` — Predictable Randomness  *(Severity: High · Status: Unresolved)*

Randomness is derived from on-chain values that are predictable, allowing users to influence outcomes in the card system.

**Recommendation:** Use a verifiable randomness source like Chainlink VRF to ensure secure and unpredictable outcomes.


### `CP-03` — Dependency Replacement Risk  *(Severity: High · Status: Unresolved)*

The deployer can change the address of the external contract that governs token transfers, allowing a malicious actor to redirect or halt all token movements.

**Recommendation:** Restrict the ability to change external dependencies to a multi-signature wallet with a mandatory delay period.


### `CP-01` — Privileged Minting Capability  *(Severity: Medium · Status: Unresolved)*

The deployer and mirror roles can increase the total token supply through initialize, mirrorTransfer, and compose functions, which may dilute existing holders.

**Recommendation:** Implement a hard cap on total supply or require a time-locked governance vote for any minting operations.


### `CP-07` — Centralized Fee Control  *(Severity: Medium · Status: Unresolved)*

Privileged roles can arbitrarily modify transfer fees, which directly impacts the economic utility of the token.

**Recommendation:** Define fee ranges in the contract logic and enforce them to prevent excessive or predatory fee adjustments.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x629d…eb5c — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CD-01` — Rounding Loss via Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

Calculations in _update and related functions perform division before multiplication, leading to precision loss.

**Recommendation:** Reorder operations to perform multiplication before division to maintain precision.


### `CP-08` — Arbitrary Limit Modification  *(Severity: Low · Status: Unresolved)*

Privileged roles can change transaction and wallet limits, potentially leading to unexpected restrictions on user activity.

**Recommendation:** Hardcode reasonable limits or implement a transparent, public process for parameter adjustments.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 97.5% of supply. What remains: 10.4% in wallets, 87.0% in other contracts. 43 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

43 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $25K (DexScreener, all pools). 24h trading volume $95K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $25K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x03ed...f512`](https://etherscan.io/address/0x03edbab5c3a0456567d61ab7f34f3b7e490ef512) |
| **Network** | Ethereum |
| **Price** | $2.4800 |
| **24h Volume** | $95.4K |
| **Liquidity** | $24.5K |
| **Volume / Liquidity** | 3.9× |
| **Token Age** | 8h |
| **Top-10 Holders** | 97.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 287 buys / 185 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x38ee8313d2d8dd1a14d451ad209d4334b43b8c2c718c1c572f6d6c6fe7edafaf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/un1corn-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
