---
token: Flip
ticker: FLIP
network: bsc
risk_score: 20
status: low
date: 2026-11-01
---

# Flip (FLIP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/flip-bsc)

---

## Audit Summary

The QuickLaunchToken is a standard ERC-20 implementation deployed on the BNB Smart Chain. The contract follows the OpenZeppelin standard library and lacks any custom privileged functions, administrative backdoors, or complex logic. The codebase is clean and adheres to industry-standard practices for token deployment.

> **Final Recommendation:** The contract is secure and follows standard practices. No further action is required for the current implementation.

For future deployments, ensure that any added functionality (such as minting or burning) is protected by robust access control mechanisms like Ownable or AccessControl to prevent unauthorized state changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows a standard ERC-20 pattern (7.1 Architecture) with no deviations from the expected interface. Code security (7.2) is high due to the use of audited OpenZeppelin libraries and… |
| **Governance / Economics** | 2/10 | High | Economic (7.4) and Governance (7.5) risks are minimal because the token does not implement any deflationary, inflationary, or voting mechanisms. The token functions purely as a standard asset without… |
| **Upgrades** | 8/10 | Low | The contract is not a proxy (7.7 Upgrades) and is therefore immutable. This eliminates risks associated with implementation changes or malicious upgrades. The logic is fixed at deployment, ensuring… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xf3de…2b75 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 22.5% of supply. What remains: 17.6% in wallets, 4.8% in other contracts. The deployer/owner wallet itself holds 2.8%. 2,283 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Flip (FLIP), market cap $1M, rank #2733. 2,283 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $107K (GeckoTerminal, all pools). 24h trading volume $29K (CoinGecko, all markets, daily snapshot). 24h trading volume $41K (GeckoTerminal, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $107K of DEX liquidity across 20 pools. Launch: 19 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 19 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 19 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x96e5...02bf`](https://bscscan.com/address/0x96e562b76905b3892f847776ba1a54883cde02bf) |
| **Network** | BNB Chain |
| **Price** | $0.00156691 |
| **24h Volume** | $40.7K |
| **Liquidity** | $106.1K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 19d |
| **Top-10 Holders** | 22.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 223 buys / 128 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x96e562b76905b3892f847776ba1a54883cde02bf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/flip-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
