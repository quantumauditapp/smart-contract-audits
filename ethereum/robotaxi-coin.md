---
token: Robotaxi Coin
ticker: ROBOTAXI
network: ethereum
risk_score: 65
status: high
date: 2026-10-28
---

# Robotaxi Coin (ROBOTAXI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/robotaxi-coin-eth)

---

## Audit Summary

The BaseToken contract is a standard ERC-20 implementation with burnable capabilities. The ownership has been renounced, meaning no administrative functions can be executed, effectively locking the contract configuration. The codebase relies on OpenZeppelin standards, which are widely audited and secure.

> **Final Recommendation:** The contract is secure and immutable. No further action is required as the ownership is renounced and the code follows industry-standard practices.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows the standard OpenZeppelin ERC-20 and ERC-20Burnable patterns, ensuring high compatibility with DeFi protocols. Code security is robust due to the use of well-tested libraries… |
| **Governance / Economics** | 2/10 | High | The protocol does not feature governance or complex economic mechanisms. Ownership has been renounced, preventing any future changes to the contract parameters. The token functions as a simple store… |
| **Upgrades** | 6/10 | Medium | The contract is not a proxy and does not support upgradeability. The code is immutable, providing high security against unauthorized logic changes. No upgrade paths exist. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0x4789…c463) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 33.7% of supply. What remains: 10.2% in wallets, 23.4% in other contracts. 274 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

274 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $66K (DexScreener, all pools). 24h trading volume $195K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $66K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9b6a...2423`](https://etherscan.io/address/0x9b6a3993a4ae6c09a29be1ba04e76c9ea55a2423) |
| **Network** | Ethereum |
| **Price** | $0.0001877 |
| **24h Volume** | $195.3K |
| **Liquidity** | $66.0K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 6h |
| **Top-10 Holders** | 33.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 536 buys / 403 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x6c4ce07937f215e2197fb16b332774e1f52bb54eca7dc01407699635f84d1a73)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/robotaxi-coin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
