---
token: Felysyum
ticker: FELY
network: polygon
risk_score: 53
status: medium
date: 2026-10-20
---

# Felysyum (FELY) — Smart Contract Security Analysis | Polygon

> **Risk Score: 53/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/felysyum-poly)

---

## Audit Summary

The Felysyum contract is a standard ERC-20 token implementation utilizing OpenZeppelin's Ownable and ERC20 libraries. The codebase is clean, follows standard patterns, and lacks complex logic or external dependencies that typically introduce vulnerabilities. No security issues were identified during the static analysis of the provided source code.

> **Final Recommendation:** The contract is secure and follows best practices for a standard ERC-20 token. No immediate changes are required for the current implementation.

For future development, ensure that any added functionality (such as minting or burning) is thoroughly tested and that ownership is transferred to a multi-signature wallet or a DAO contract to mitigate risks associated with single-point-of-failure EOA control.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows standard ERC-20 patterns (7.1 Architecture). Code security is robust due to the use of audited OpenZeppelin libraries (7.2 Code Security). Access control is limited to… |
| **Governance / Economics** | 1/10 | High | The economic model is a standard token with no inflationary or deflationary mechanics (7.4 Economic). Governance is centralized under the owner (7.5 Governance). Operations are straightforward with… |
| **Upgrades** | 5/10 | Medium | The contract is not upgradeable (7.7 Upgrades). The logic is immutable, which eliminates risks associated with proxy patterns or logic updates. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 40.6% — UNCX Locker |
| **Top-1 Unlocked Holder** | ⚠️ 57.4% |
| **Top-3 Unlocked** | 59.4% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 21.8% still sits in UNCX Locker, but that lock expired on 27 Sep 2026 — its owner can withdraw it at any moment. 12.6% still sits in UNCX Locker, but that lock expired on 30 Jun 2026 — its owner can withdraw it at any moment. 4.6% still sits in UNCX Locker, but that lock expired on 15 May 2026 — its owner can withdraw it at any moment. 1.3% still sits in UNCX Locker, but that lock expired on 10 Oct 2025 — its owner can withdraw it at any moment. 0.3% still sits in UNCX Locker, but that lock expired on 02 Dec 2025 — its owner can withdraw it at any moment. 2.0% is held, unlocked, by the token's owner/deployer (0xabc1…7f1e) — they can pull that liquidity at any moment. This is the rug-pull path. 57.4% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x3e54…7baf — holds 57.4% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 95.8% of supply. What remains: 0.0% in wallets, 95.8% in other contracts. 10,672 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Felysyum (FELY), market cap $19M, rank #871. 10,672 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.3M (DexScreener, all pools). 24h trading volume $1.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $88K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.3M of DEX liquidity across 2 pools. Launch: 689 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xee99...0824`](https://polygonscan.com/address/0xee997788f625809332baabb3110bcf1ba7400824) |
| **Network** | Polygon |
| **Price** | $0.438 |
| **24h Volume** | $88.5K |
| **Liquidity** | $1.29M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 95.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 49 buys / 71 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0xc810868393de87e0daa3b1f4e90c6738192d2a06)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/felysyum-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
