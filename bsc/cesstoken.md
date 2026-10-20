---
token: CESSToken
ticker: CESS
network: bsc
risk_score: 47
status: medium
date: 2026-10-01
---

# CESSToken (CESS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 47/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cesstoken-bsc)

---

## Audit Summary

The CESSToken contract is a standard ERC-20 token implementation on the BSC network. The audit found no critical, high, medium, or low severity vulnerabilities. The contract exhibits a decentralized design with no privileged functions impacting core token transfers, indicating a robust and secure implementation.

> **Final Recommendation:** Users and token holders should be aware that while the contract itself is robust, general blockchain security practices remain crucial. Always verify the contract address for any interactions and exercise caution with external platforms or protocols integrating this token. Ensure private keys are secured and be vigilant against phishing attempts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The CESSToken contract is a robust implementation of the ERC-20 standard, providing essential token functionalities such as `transfer` and `balanceOf` (7.1 Architecture). The absence of any… |
| **Governance / Economics** | 3/10 | High | The contract features a highly decentralized governance model, as no specific roles or addresses possess the ability to control or alter core token parameters (7.5 Governance). This design… |
| **Upgrades** | 8/10 | Low | The CESSToken contract is not deployed as a proxy and therefore lacks upgradeability features (7.7 Upgrades). This immutability eliminates all risks associated with upgrade mechanisms, such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xb583…06f0 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.9% of supply. Of that, 3.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 89.8% in wallets, 1.0% in other contracts. 55,605 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as CESS Network (CESS), market cap $6M, rank #1652. 55,605 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $850K (DexScreener, all pools). 24h trading volume $1.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $366K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $850K of DEX liquidity across 1 pools. Launch: 462 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0c78...3462`](https://bscscan.com/address/0x0c78d4605c2972e5f989de9019de1fb00c5d3462) |
| **Network** | BNB Chain |
| **Price** | $0.002159 |
| **24h Volume** | $366.4K |
| **Liquidity** | $850.0K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 93.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3615 buys / 1662 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xada2d09b25bb7efd1b4fbe3b779117a9e98593c3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cesstoken-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
