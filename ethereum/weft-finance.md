---
token: Weft Finance
ticker: WEFT
network: ethereum
risk_score: 63
status: medium
date: 2026-10-20
---

# Weft Finance (WEFT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 63/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/weft-finance-eth)

---

## Audit Summary

BaseToken is a standard ERC-20 implementation with burnable capabilities. The contract ownership has been renounced, meaning no administrative functions can be executed, effectively locking the current configuration. The codebase follows standard OpenZeppelin patterns, ensuring high compatibility and reliability.

> **Final Recommendation:** The contract is secure and immutable. No further action is required for the current deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes standard OpenZeppelin ERC-20 libraries, which are battle-tested and secure. 7.1 Architecture and 7.2 Code Security are robust, adhering to modern Solidity standards. 7.3… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are static due to the renounced ownership. There are no inflationary mechanisms or governance-controlled parameters that could impact token holders. The token… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable, providing certainty to users that the contract behavior will not change. 7.8 Operations are straightforward and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0xc3e1…a331) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 30.4% of supply. What remains: 7.7% in wallets, 22.7% in other contracts. 347 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

347 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $65K (DexScreener, all pools). 24h trading volume $475K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $65K of DEX liquidity across 4 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbdbe...7f89`](https://etherscan.io/address/0xbdbef668fda6883df73192b813b6bf760fd07f89) |
| **Network** | Ethereum |
| **Price** | $0.0001593 |
| **24h Volume** | $475.5K |
| **Liquidity** | $64.8K |
| **Volume / Liquidity** | 7.3× |
| **Token Age** | 11h |
| **Top-10 Holders** | 30.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 785 buys / 528 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xc3b2e57ad2a30d7d9bf9fe2651b63e24ba1d11873bc7a48df1bf687cda15f247)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/weft-finance-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
