---
token: SpaceXSI
ticker: SPACEXSI
network: ethereum
risk_score: 15
status: low
date: 2026-10-09
---

# SpaceXSI (SPACEXSI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacexsi-eth)

---

## Audit Summary

The LaunchToken contract implements a standard ERC-20 token with no special features, privileged roles, or complex logic. The audit found no specific vulnerabilities or deviations from standard ERC-20 behavior. The contract is not upgradeable, ensuring fixed and predictable behavior.

> **Final Recommendation:** Given the contract's simplicity as a standard ERC-20 token, the primary recommendations focus on external factors. Ensure that the token's deployment parameters, such as initial supply and distribution, align with the project's economic model. For any integrations with other protocols, thoroughly audit those external systems, as the security of a simple token often depends on the security of the systems it interacts with.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The LaunchToken contract is a straightforward implementation of the ERC-20 standard (7.1 Architecture). It includes all required ERC-20 functions such as `transfer` and `approve`. Static analysis… |
| **Governance / Economics** | 7/10 | Low | As a standard ERC-20 token, LaunchToken does not incorporate any complex governance mechanisms or specific economic models beyond its fungible nature (7.5 Governance). The token's value and utility… |
| **Upgrades** | 9/10 | Low | The LaunchToken contract is deployed as a standard, non-upgradeable contract (7.7 Upgrades). This design choice eliminates all risks associated with upgrade mechanisms, such as proxy implementation… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 56.2% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x3a9d…fa1f — holds 56.2% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 93% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 34.4% of supply. What remains: 16.3% in wallets, 18.2% in other contracts. 277 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

277 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $58K (DexScreener, all pools). 24h trading volume $128K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $58K of DEX liquidity across 4 pools. Launch: 8 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 8 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 8 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa562...13c3`](https://etherscan.io/address/0xa562ee15460cfc8c7a71920b25fa13bd8c5313c3) |
| **Network** | Ethereum |
| **Price** | $0.0002018 |
| **24h Volume** | $123.9K |
| **Liquidity** | $53.9K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 8d |
| **Top-10 Holders** | 34.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 275 buys / 214 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x61b30b9cf6f6a781bda5a15bd5809cc86363aaf5554e107f0533b02396baf9d0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacexsi-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*
