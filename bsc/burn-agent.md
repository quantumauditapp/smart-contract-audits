---
token: Burn Agent
ticker: BURN
network: bsc
risk_score: 79
status: high
date: 2026-11-03
---

# Burn Agent (BURN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 79/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/burn-agent-bsc)

---

## Audit Summary

The BurnAgentMixed contract implements an ERC-20 token with custom minting and transfer control logic. The protocol relies on privileged roles (earlyopener, idcollection) to manage supply and transfer availability. While the core ERC-20 implementation is standard, the centralization of control over token issuance and transferability poses a significant risk to token holders.

> **Final Recommendation:** It is recommended to implement a multi-signature wallet or a decentralized governance contract to manage the privileged roles, reducing the risk of a single point of failure. Additionally, consider adding a timelock for any administrative changes to transfer rules to provide transparency to the community.

For mathematical operations, ensure that all multiplication occurs before division to maintain precision. Consider using a library like ABDKMath64x64 or OpenZeppelin's Math library to handle fixed-point arithmetic safely.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes ReentrancyGuard to protect sensitive functions, which is a strong security practice. Code structure is modular, separating minting logic from standard ERC-20 operations.… |
| **Governance / Economics** | 3/10 | High | The protocol exhibits high centralization, as privileged addresses have the authority to mint tokens and halt transfers at will. This creates a trust-based model where holders are vulnerable to… |
| **Upgrades** | 4/10 | Medium | The contract is not implemented as a proxy and is therefore immutable. This eliminates risks associated with logic upgrades or proxy storage collisions. The current state is fixed, providing… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.3% (≈ permanent lock) |
| **LP Locked** | 99.3% — Null Address |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The functions mint, mintWithInviter, and openEarly allow privileged addresses to create new tokens at will. This can lead to significant supply inflation and dilution of existing token holders' value.

**Recommendation:** Implement a hard cap on the total supply or transition the minting authority to a decentralized governance contract.


### `CP-05` — Administrative Control Over Transfers  *(Severity: Medium · Status: Unresolved)*

Privileged addresses can toggle a switch that determines whether token transfers are permitted. This allows administrators to freeze user funds or restrict market liquidity arbitrarily.

**Recommendation:** Remove the transfer-blocking functionality or implement a community-voted mechanism to trigger such restrictions.


### `CD-01` — Precision Loss in Calculations  *(Severity: Low · Status: Unresolved)*

The functions _oracle and priceAt perform division before multiplication, which results in rounding errors. This can lead to inaccurate pricing and potential economic discrepancies.

**Recommendation:** Rearrange the mathematical operations to perform multiplication before division, ensuring that intermediate values do not overflow.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 55.0% of supply. Of that, 5.3% burned, 41.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 3.4% in wallets, 5.2% in other contracts. 584 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

584 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.3% of the pool's LP is burned or time-locked. 99.3% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.7% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $41K (DexScreener, all pools). 24h trading volume $258K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $41K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7de1...b1c4`](https://bscscan.com/address/0x7de1606230aa70802caecf1a3e90039a6265b1c4) |
| **Network** | BNB Chain |
| **Price** | $0.00000012 |
| **24h Volume** | $257.7K |
| **Liquidity** | $41.1K |
| **Volume / Liquidity** | 6.3× |
| **Token Age** | 13h |
| **Top-10 Holders** | 55.0% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 3407 buys / 3061 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x53895464c524c6fdd82ad5189bf92d9b798c6a51)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/burn-agent-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
