---
token: AIPRO
ticker: AIPRO
network: bsc
risk_score: 52
status: medium
date: 2026-11-02
---

# AIPRO (AIPRO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 52/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aipro-bsc)

---

## Audit Summary

The LaunchToken is a standard ERC-20 implementation deployed as an EIP-1167 minimal clone. The contract includes centralized administrative controls that allow the minter to mint tokens, block addresses, and toggle transfer restrictions. While the code follows standard patterns, the high degree of centralization poses a significant risk to token holders.

> **Final Recommendation:** The protocol should transition administrative powers to a multi-signature wallet or a decentralized governance contract to mitigate single-point-of-failure risks. Implementing a timelock on privileged functions would provide transparency and protection for token holders against sudden administrative actions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a clean, standard ERC-20 implementation with 7.1 Architecture following the EIP-1167 clone pattern. 7.2 Code Security is maintained through the use of OpenZeppelin-style… |
| **Governance / Economics** | 3/10 | High | The protocol exhibits high 7.4 Economic and 7.5 Governance risks due to the concentration of power in the minter role. The minter can arbitrarily dilute supply via minting and restrict liquidity by… |
| **Upgrades** | 4/10 | Medium | The contract is deployed as an EIP-1167 minimal clone, which is immutable by design. 7.7 Upgrades are not possible, ensuring the logic remains fixed. 7.8 Operations are stable as the implementation… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.9% (≈ permanent lock) |
| **LP Locked** | 99.9% — Null Address |

## Security Findings

_🟡 3 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The minter role has the authority to mint new tokens, which can dilute the value of existing holdings. This function is restricted to a privileged address.

**Recommendation:** Restrict minting to a capped amount or transition the minter role to a DAO-controlled contract.


### `CP-05` — Transfer Restriction Switch  *(Severity: Medium · Status: Unresolved)*

The minter can call disableBlocks to toggle a switch that prevents all token transfers. This effectively allows the controller to freeze the entire market for this token.

**Recommendation:** Remove the ability to disable global transfers or implement a community-voted mechanism for such actions.


### `CP-06` — Address Blacklisting Capability  *(Severity: Medium · Status: Unresolved)*

The minter can use setPoolBlocked to prevent specific addresses from transferring tokens. This allows the controller to censor individual users or liquidity pools.

**Recommendation:** Limit the use of blacklisting to specific regulatory compliance scenarios and ensure the process is transparent.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 83.3% of supply. Of that, 17.8% burned, 54.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 8.5% in wallets, 2.7% in other contracts. 432 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

432 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.9% of the pool's LP is burned or time-locked. 99.9% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.1% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $24K (DexScreener, all pools). 24h trading volume $215K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: minter — a contract. Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $24K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x577b...b286`](https://bscscan.com/address/0x577bea203e5326ff6e1d4594a94167111836b286) |
| **Network** | BNB Chain |
| **Price** | $0.00000002 |
| **24h Volume** | $214.6K |
| **Liquidity** | $23.8K |
| **Volume / Liquidity** | 9.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | 83.3% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 2239 buys / 2832 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x9ace87f96f41aa902688362e2387fbf7b3fbb91f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aipro-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
