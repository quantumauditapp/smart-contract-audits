---
token: AGENT ID
ticker: AID
network: bsc
risk_score: 53
status: medium
date: 2026-11-01
---

# AGENT ID (AID) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 53/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/agent-id-bsc-22cc)

---

## Audit Summary

LaunchToken is an EIP-1167 minimal clone implementation of an ERC-20 token. The contract includes centralized administrative controls that allow a designated minter to mint tokens, block specific addresses, and toggle global transfer restrictions. While the core ERC-20 logic follows standard patterns, the presence of these privileged functions introduces significant centralization risk for token holders.

> **Final Recommendation:** Investors should be aware that the minter role holds absolute authority over the token's supply and transferability. It is recommended to transition the minter role to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single compromised key. 

Additionally, consider implementing a timelock for sensitive operations like blocking addresses or disabling transfers to provide transparency and a window for community response. Ensure that the minter address is secured with robust institutional-grade custody solutions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin-style ERC-20 logic, ensuring compatibility with common DeFi protocols. 7.1 Architecture is based on a secure EIP-1167 clone pattern, while 7.2 Code… |
| **Governance / Economics** | 3/10 | High | The economic model is heavily centralized, granting the minter total control over supply and liquidity access. 7.4 Economic stability is subject to the minter's discretion regarding supply inflation… |
| **Upgrades** | 4/10 | Medium | The contract is deployed as an EIP-1167 minimal clone, which is immutable by design. 7.7 Upgrades are not possible, as the implementation logic is hardcoded into the proxy's bytecode. This eliminates… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.8% (≈ permanent lock) |
| **LP Locked** | 99.8% — Null Address |

## Security Findings

_🟡 3 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The minter address has the ability to create new tokens at will, up to a defined maximum supply. This allows the controller to dilute the holdings of all existing token holders.

**Recommendation:** Restrict the minting capability to a multi-signature wallet or a decentralized governance contract to prevent unilateral supply inflation.


### `CP-05` — Global Transfer Restriction Switch  *(Severity: Medium · Status: Unresolved)*

The minter can trigger a function to disable transfers globally. This effectively freezes the token's liquidity and prevents users from moving or selling their assets.

**Recommendation:** Remove the ability to globally disable transfers or implement a timelock that notifies the community before such a drastic action is taken.


### `CP-06` — Address Blacklisting Capability  *(Severity: Medium · Status: Unresolved)*

The minter can add specific addresses to a blacklist, preventing those users from transferring or selling their tokens. This creates a risk of censorship and loss of access to funds for targeted users.

**Recommendation:** Limit the use of blacklisting to specific regulatory compliance scenarios and ensure the process is transparent and auditable.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 60.6% of supply. Of that, 24.7% burned, 22.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.2% in wallets, 3.9% in other contracts. 682 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

682 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.8% of the pool's LP is burned or time-locked. 99.8% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.2% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $26K (DexScreener, all pools). 24h trading volume $361K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: minter — a contract. Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $26K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa691...67fe`](https://bscscan.com/address/0xa691cbfe81d3b8708f89889d3cdfb8796ddf67fe) |
| **Network** | BNB Chain |
| **Price** | $0.00000006 |
| **24h Volume** | $361.1K |
| **Liquidity** | $26.1K |
| **Volume / Liquidity** | 13.8× |
| **Token Age** | 18h |
| **Top-10 Holders** | 60.6% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 4163 buys / 3856 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xc985e99806fbfd06aa157918753e83d8054ce822)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/agent-id-bsc-22cc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
