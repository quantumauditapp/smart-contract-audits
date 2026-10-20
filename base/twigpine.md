---
token: Twigpine
ticker: TWIG
network: base
risk_score: 33
status: low
date: 2026-10-02
---

# Twigpine (TWIG) — Smart Contract Security Analysis | Base

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/twigpine-base)

---

## Audit Summary

The TwigWrapper contract is an ERC20 wrapper implementation. Static analysis and review of key functions revealed no critical, high, or medium severity vulnerabilities. The contract operates as a standard token wrapper without any privileged roles or complex state-changing logic that could introduce security risks.

> **Final Recommendation:** The TwigWrapper contract appears to be a well-implemented, standard ERC20 wrapper with no identified vulnerabilities. For future deployments, ensure that any interactions with external contracts (7.6) are carefully vetted for potential attack vectors. Maintain robust operational security practices (7.8) for any associated off-chain components or user interfaces.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The TwigWrapper contract implements standard ERC20 functionality and acts as a wrapper. Its architecture (7.1) is straightforward, inheriting from ERC20Wrapper and ERC20, ensuring basic token… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a low governance and economic risk profile (7.4, 7.5) due to the absence of any privileged functions or special roles. This means no single entity or group has the ability to… |
| **Upgrades** | 8/10 | Low | The TwigWrapper contract is not designed as an upgradeable proxy (7.7), meaning its logic cannot be changed post-deployment. This eliminates risks associated with upgrade mechanisms, such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 82.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0x8d65…db2e — holds 82.3% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 58% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 81.6% of supply. What remains: 22.2% in wallets, 59.4% in other contracts. 139 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

139 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $52K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $22K of DEX liquidity across 4 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6ac1...13c1`](https://basescan.org/address/0x6ac18bcf4ede02591d4917452700ea5eaaea13c1) |
| **Network** | Base |
| **Price** | $0.00002462 |
| **24h Volume** | $40.2K |
| **Liquidity** | $12.6K |
| **Volume / Liquidity** | 3.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | 81.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 241 buys / 291 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x1f5b05e16259a7e2529d4a2fe4baa5f230c4b2b144652693f7c662b2e47aa0d6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/twigpine-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-02*
