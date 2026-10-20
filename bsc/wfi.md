---
token: WFI
ticker: WFI
network: bsc
risk_score: 43
status: medium
date: 2026-10-06
---

# WFI (WFI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wfi-bsc)

---

## Audit Summary

The WFI contract is an ERC-20 token implementation with standard functionalities and an Ownable2Step ownership pattern. The contract does not contain complex logic that could introduce high technical or economic risks. No critical or high-severity vulnerabilities were identified during the audit.

> **Final Recommendation:** Ensure the private key controlling the owner address is secured with robust multi-factor authentication and cold storage solutions, as it controls the administrative functions of the token. Conduct thorough testing of all contract functionalities on a testnet before any mainnet deployment to confirm expected behavior and prevent operational issues.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The WFI contract implements the ERC-20 standard, including ERC20Permit for gasless approvals. Its architecture is straightforward, inheriting from ERC20 and Ownable2Step. The core ERC-20 functions… |
| **Governance / Economics** | 3/10 | High | The contract utilizes the Ownable2Step pattern, allowing the owner to securely transfer ownership via a two-step process (7.3 Access Control). The owner's control is limited to administrative… |
| **Upgrades** | 6/10 | Medium | The WFI contract is not deployed as a proxy (7.7 Upgrades). Therefore, it does not possess any upgradeability mechanisms. This means the contract's logic is immutable once deployed, eliminating… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 20.7% |
| **Top-3 Unlocked** | 41.9% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 70.0% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 96.9% of supply. What remains: 5.6% in wallets, 91.3% in other contracts. 33,197 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as WeFi (WFI). 33,197 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $37K (DexScreener, all pools). 24h trading volume $2.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $175K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $37K of DEX liquidity across 5 pools. Launch: 677 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x90c4...dd6f`](https://bscscan.com/address/0x90c48855bb69f9d2c261efd0d8c7f35990f2dd6f) |
| **Network** | BNB Chain |
| **Price** | $2.1800 |
| **24h Volume** | $174.6K |
| **Liquidity** | $36.8K |
| **Volume / Liquidity** | 4.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 96.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 203 buys / 190 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xdbbb8c123f0ee395efcaaf6b3285562470ab40e0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wfi-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
