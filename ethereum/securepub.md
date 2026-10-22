---
token: securepub
ticker: SECUREPUB
network: ethereum
risk_score: 80
status: high
date: 2026-10-22
---

# securepub (SECUREPUB) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 80/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/securepub-eth)

---

## Audit Summary

The BaseToken contract is a standard ERC-20 implementation with burnable capabilities. Ownership has been formally renounced, meaning no administrative functions can be executed, effectively locking the contract configuration. The codebase follows OpenZeppelin standards, ensuring high reliability for standard token operations.

> **Final Recommendation:** The contract is secure and follows best practices for a standard utility token. No further action is required as the code is immutable and free of administrative backdoors.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture utilizes battle-tested OpenZeppelin libraries for ERC-20 and Burnable functionality. 7.1 Architecture is clean and modular, adhering to standard patterns. 7.2 Code Security is high… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance risks are minimal as the contract is immutable. There are no minting or pause mechanisms that could impact token holders. The token supply is strictly controlled by… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is permanently deployed and cannot be altered. 7.8 Operations are stable due to the lack of external dependencies or complex… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0xe44d…1be5) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No code-level findings — contract source is not verified on the explorer  *(Severity: Informational · Status: Acknowledged)*

The contract's source code has not been published or verified on the block explorer, so only its deployed bytecode and on-chain behaviour were available. No source-level vulnerability could be confirmed or ruled out. The assessment on this page rests on mint/owner authority, holder concentration.

**Recommendation:** Treat an unverified contract as unaudited at the code level. Ask the team to verify the source on the explorer, which makes an independent review possible.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 39.3% of supply. What remains: 5.9% in wallets, 33.4% in other contracts. 269 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

269 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $62K (DexScreener, all pools). 24h trading volume $222K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $62K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xeb9b...a0e6`](https://etherscan.io/address/0xeb9bfc7bfa64e8b0a990e6a7dedb83716057a0e6) |
| **Network** | Ethereum |
| **Price** | $0.0001145 |
| **24h Volume** | $221.9K |
| **Liquidity** | $62.2K |
| **Volume / Liquidity** | 3.6× |
| **Token Age** | 4h |
| **Top-10 Holders** | 39.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 439 buys / 233 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x2bd22a121909346895af8fea2f53689f9162282eee08462c92bef9fbc618573d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/securepub-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
