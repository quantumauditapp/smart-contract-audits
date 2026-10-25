---
token: Nigga Its Over
ticker: NIO
network: ethereum
risk_score: 64
status: medium
date: 2026-10-25
---

# Nigga Its Over (NIO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nigga-its-over-eth)

---

## Audit Summary

BaseToken is a standard ERC-20 implementation with burnable capabilities. The contract ownership has been renounced, meaning no administrative functions can be executed, effectively locking the current configuration. The codebase relies on standard OpenZeppelin libraries, ensuring high compatibility and security standards.

> **Final Recommendation:** The contract is secure and follows standard implementation patterns. No further action is required as the ownership is renounced and the code is immutable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin ERC-20 and Burnable standards. 7.1 Architecture is standard, 7.2 Code Security is high due to the use of modern Solidity 0.8.x, and 7.3 Access Control… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance risks are minimal as the contract is immutable and ownership is renounced. There are no minting functions or inflationary mechanisms present. The token supply is fixed… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the contract is not a proxy. 7.8 Operations are straightforward, relying on standard ERC-20 functionality. The contract is permanently fixed in its current state. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0xeb2b…4374) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 35.9% of supply. What remains: 9.1% in wallets, 26.8% in other contracts. 186 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

186 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $79K (DexScreener, all pools). 24h trading volume $166K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $79K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe020...a949`](https://etherscan.io/address/0xe020b7fb53ef7324708b6fb4d88920e5c4f9a949) |
| **Network** | Ethereum |
| **Price** | $0.0001759 |
| **24h Volume** | $166.3K |
| **Liquidity** | $79.4K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 1h |
| **Top-10 Holders** | 35.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 346 buys / 217 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xe2e70d8c613c6db5a624008655a2f2c8753a78beba64d84361a714d0dc085925)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nigga-its-over-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
