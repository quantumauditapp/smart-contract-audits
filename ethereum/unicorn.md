---
token: Unicorn
ticker: UNICORN
network: ethereum
risk_score: 84
status: high
date: 2026-10-25
---

# Unicorn (UNICORN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/unicorn-eth)

---

## Audit Summary

The RobinVistaToken is a standard ERC20 implementation utilizing a factory-based initialization pattern. The contract logic is clean and relies on audited OpenZeppelin libraries. No critical vulnerabilities were identified; however, the initialization pattern requires careful handling to prevent unauthorized state setting.

> **Final Recommendation:** Ensure the factory contract is deployed securely and that the initialization parameters are validated before calling the initialize function. Monitor the factory for any potential unauthorized access to the setPool function.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows a standard factory-clone pattern (7.1). Code security is high due to the use of OpenZeppelin's battle-tested ERC20 implementation (7.2). Access control is correctly… |
| **Governance / Economics** | 1/10 | High | Economic parameters are defined at initialization (7.4). Governance is centralized within the factory contract (7.5). Operations are straightforward with no complex staking or lending logic (7.8). |
| **Upgrades** | 2/10 | High | The contract uses a proxy pattern (7.7). Upgrades are managed via the factory, which is standard for this architecture. No specific upgrade logic is exposed in the token contract itself. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0xeebb…ee84) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `M-01` — Initialization Front-running  *(Severity: Medium · Status: Unresolved)*

The initialize function is public and lacks protection against front-running. An attacker could potentially call initialize before the intended deployer, setting arbitrary parameters.

**Recommendation:** Ensure the factory contract calls the initialize function immediately after deployment in the same transaction.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `L-01` — Lack of Zero Address Validation  *(Severity: Low · Status: Unresolved)*

The setPool function does not validate that the baseToken address is not the zero address.

**Recommendation:** Add a require(baseToken_ != address(0), 'Invalid address') check.


### `I-01` — Metadata Immutability  *(Severity: Informational · Status: Unresolved)*

Token metadata (name, symbol) is set during initialization and cannot be updated, which is standard but limits flexibility.

**Recommendation:** None required; this is a design choice.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 47.4% of supply. What remains: 22.0% in wallets, 25.4% in other contracts. The deployer/owner wallet itself holds 5.6%. 86 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

86 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $31K (DexScreener, all pools). 24h trading volume $80K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $31K of DEX liquidity across 5 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1040...44de`](https://etherscan.io/address/0x104087d3e23849900636d2d0cba0adff04d744de) |
| **Network** | Ethereum |
| **Price** | $0.00007877 |
| **24h Volume** | $79.4K |
| **Liquidity** | $30.9K |
| **Volume / Liquidity** | 2.6× |
| **Token Age** | 12h |
| **Top-10 Holders** | 47.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 312 buys / 167 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xbfd2e37839980a8135998ce2b21d239ef522f0a6234aabeb75815e4a59668466)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/unicorn-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
