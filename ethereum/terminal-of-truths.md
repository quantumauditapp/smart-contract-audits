---
token: terminal of truths
ticker: TRUTH
network: ethereum
risk_score: 62
status: medium
date: 2026-10-23
---

# terminal of truths (TRUTH) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/terminal-of-truths-eth)

---

## Audit Summary

The contract at the provided address is not verified on the block explorer, preventing any technical review of the source code. While ownership has been renounced, the lack of transparency regarding token logic, tax mechanisms, or minting capabilities poses a significant risk to holders. Investors should exercise extreme caution as the underlying mechanics remain opaque.

> **Final Recommendation:** Do not interact with or provide liquidity to this contract until the source code is verified on a block explorer. The combination of unverified code and unlocked liquidity is a primary indicator of high-risk assets.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown due to lack of source code. 7.2 Code Security: Cannot be audited; potential for hidden backdoors or malicious functions exists. 7.3 Access Control: Ownership is renounced… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic: Liquidity is currently unlocked, creating a high risk of rug-pull scenarios. 7.5 Governance: No formal governance structure is visible. The tokenomics are opaque, and there is no… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The contract does not appear to be a proxy, suggesting it is immutable. However, without source code, it is impossible to confirm if the contract contains self-destruct or upgrade-like… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published, making it impossible to verify the logic, security, or safety of the token.

**Recommendation:** Verify the contract source code on the block explorer to allow for community and security review.


### `H-01` — Unlocked Liquidity  *(Severity: High · Status: Unresolved)*

Liquidity is currently unlocked, allowing for the potential removal of all backing assets by the deployer or any party with control over the liquidity pool.

**Recommendation:** Lock liquidity in a reputable time-locked vault or burn the liquidity provider tokens.


### `M-01` — Lack of Transparency  *(Severity: Medium · Status: Unresolved)*

The absence of verified code prevents users from understanding tax mechanisms, transfer restrictions, or potential minting functions.

**Recommendation:** Publish a whitepaper or documentation detailing the tokenomics and contract functionality.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The holder list from the security indexer adds up to 149.5% of supply, so it does not describe real balances. That happens with rebasing and reflection tokens, whose balances change without transfers, and with contracts that report balances they do not hold. Concentration is unknown and priced as an unknown — neither a whale nor safe.

**Recommendation:** Check the largest holders on the block explorer, which reads current balances.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

135 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $27K (DexScreener, all pools). 24h trading volume $78K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $27K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbd40...3103`](https://etherscan.io/address/0xbd40dc0fce25c3637c8ac7c4428106d097173103) |
| **Network** | Ethereum |
| **Price** | $0.00001818 |
| **24h Volume** | $77.8K |
| **Liquidity** | $27.5K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 293 buys / 181 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x62663bd635e021c2cd3300a22d1bd2cae177ca09)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/terminal-of-truths-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
