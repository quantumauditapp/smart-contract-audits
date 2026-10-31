---
token: Drop Social
ticker: DROPS
network: bsc
risk_score: 29
status: low
date: 2026-10-31
---

# Drop Social (DROPS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/drop-social-bsc)

---

## Audit Summary

The DropSocialToken is a standard ERC-20 implementation utilizing OpenZeppelin's audited libraries. The contract lacks any privileged administrative functions, meaning it is immutable and decentralized by design. No security vulnerabilities were identified in the transfer logic or token standard compliance.

> **Final Recommendation:** The contract is secure and follows industry best practices for standard tokens. No further action is required as the code is immutable and free of known vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows standard ERC-20 patterns using battle-tested OpenZeppelin contracts. 7.1 Architecture is clean and modular, while 7.2 Code Security is high due to the lack of custom logic.… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance items are not applicable as the contract does not implement minting, burning, or voting mechanisms. The token supply is fixed upon deployment. There are no… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are straightforward and rely entirely on the underlying EVM standard. The contract is permanently immutable. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 87.1% — Null Address, UNCX |
| **Top-1 Unlocked Holder** | 12.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity only partly locked or burned  *(Severity: Medium · Status: Acknowledged)*

87.1% of the pool's LP is burned or time-locked. 87.1% is locked in UNCX until 29 May 2027 (210 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. 12.9% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.9% of supply. Of that, 0.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.4% in wallets, 74.9% in other contracts. 985 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Drop Social (DROPS), market cap $1M, rank #2929. 985 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $48K (DexScreener, all pools). 24h trading volume $36K (CoinGecko, all markets, daily snapshot). 24h trading volume $37K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $48K of DEX liquidity across 1 pools. Launch: 154 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xff0e...bd5c`](https://bscscan.com/address/0xff0e7232c902d96b57cc99e52c1056acdd64bd5c) |
| **Network** | BNB Chain |
| **Price** | $0.04234 |
| **24h Volume** | $36.5K |
| **Liquidity** | $48.1K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 90.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 184 buys / 129 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xf4e8670cb8e2a9917b4132893534345dab97d29d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/drop-social-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
