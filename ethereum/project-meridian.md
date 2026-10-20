---
token: Project meridian
ticker: MERIDIAN
network: ethereum
risk_score: 27
status: low
date: 2026-10-02
---

# Project meridian (MERIDIAN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/project-meridian-eth)

---

## Audit Summary

The LaunchToken contract is a standard ERC-20 implementation. Static analysis revealed no privileged functions or custom logic that could impact token transfers or introduce vulnerabilities. No critical or high-severity issues were identified, indicating a robust and predictable token design.

> **Final Recommendation:** Ensure that the deployment process was secure and that the contract address is correctly communicated to users. As the contract is immutable and follows a standard ERC-20 implementation, no further code-level security actions are required. Users should be aware that the token's functionality is fixed and cannot be altered post-deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract implements the ERC-20 standard without additional custom logic or privileged functions, ensuring predictable and secure token operations (7.1 Architecture, 7.2 Code Security). All… |
| **Governance / Economics** | 6/10 | Medium | The contract does not include any governance mechanisms or complex economic models beyond the basic ERC-20 token functionality (7.5 Governance, 7.4 Economic). There are no privileged roles that can… |
| **Upgrades** | 9/10 | Low | The contract is not deployed as a proxy and therefore is not upgradeable (7.7 Upgrades). This eliminates upgrade-related risks such as proxy misconfigurations or logic errors introduced during… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x87f5…3021 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 51.1% of supply. What remains: 13.3% in wallets, 37.9% in other contracts. The deployer/owner wallet itself holds 1.9%. 203 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

203 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $26K (DexScreener, all pools). 24h trading volume $165K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $26K of DEX liquidity across 3 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xac30...9fb1`](https://etherscan.io/address/0xac30876a05aece34633d9c01454e2a2947d99fb1) |
| **Network** | Ethereum |
| **Price** | $0.00005712 |
| **24h Volume** | $164.6K |
| **Liquidity** | $26.4K |
| **Volume / Liquidity** | 6.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | 51.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 551 buys / 396 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x0d0f3eea7662b5c91e412119a2d67ef2174a7585b276a28f243e19325043e4d8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/project-meridian-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-02*
