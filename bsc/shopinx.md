---
token: ShopinX
ticker: SHOPINX
network: bsc
risk_score: 93
status: critical
date: 2026-10-27
---

# ShopinX (SHOPINX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 93/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/shopinx-bsc)

---

## Audit Summary

The ShopinXToken is an ERC-20 compliant token with integrated vesting and time-lock mechanisms. The contract utilizes a centralized distribution model where a privileged 'distributor' role manages token allocation during an initial distribution phase. While the core ERC-20 logic is standard, the presence of administrative minting/distribution powers and potential rounding issues in vesting calculations present moderate risks to token holders.

> **Final Recommendation:** It is recommended to implement a multi-signature wallet for the 'distributor' role to mitigate the risk of a single point of failure during the distribution phase. Additionally, consider transitioning to a decentralized governance model or a time-locked contract to finalize the distribution phase automatically.

For the vesting logic, refactor the math to perform multiplication before division to ensure precision. Ensure that all administrative actions are documented and transparently communicated to the community to maintain trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract implements standard ERC-20 functionality with robust OpenZeppelin libraries. 7.1 Architecture is modular, separating distribution logic from standard transfers. 7.2 Code Security shows… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risks are centered on the centralized distributor's ability to influence supply during the distribution phase. 7.5 Governance is non-existent, relying entirely on the distributor… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are limited to the distribution phase, after which the contract becomes immutable regarding distribution logic. This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `CD-02` — Predictable Randomness in Vesting  *(Severity: High · Status: Unresolved)*

The vestedAmount function relies on block timestamps and on-chain state that can be influenced or predicted by miners or the distributor, potentially affecting the timing and amount of token releases.

**Recommendation:** Avoid relying on on-chain values for critical financial calculations where possible, or implement a more robust time-based verification mechanism.


### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0xd746…b5ba) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Centralized Minting and Allocation Control  *(Severity: Medium · Status: Unresolved)*

The distributor role has the power to mint and allocate tokens via batchTransfer functions. This allows the controller to significantly alter the total supply and distribution, potentially diluting existing holders if not managed transparently.

**Recommendation:** Restrict the distributor role to a multi-signature wallet and provide public documentation of the intended distribution schedule.


### `CD-01` — Rounding Loss in Vesting Calculations  *(Severity: Low · Status: Unresolved)*

The functions _validateSchedule and vestedAmount perform division before multiplication, which can lead to precision loss and minor discrepancies in the amount of tokens vested to users.

**Recommendation:** Refactor the arithmetic to perform all multiplications before divisions to maintain maximum precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 76.5% of supply. What remains: 76.5% in wallets, 0.0% in other contracts. 7,032 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as ShopinX (SHOPINX). 7,032 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $65K (DexScreener, all pools). 24h trading volume $23K (CoinGecko, all markets, daily snapshot). 24h trading volume $35K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $65K of DEX liquidity across 1 pools. Launch: 5 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 5 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 5 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4f0e...0d6b`](https://bscscan.com/address/0x4f0ed1f48beaa4797a62202a21804cadc2170d6b) |
| **Network** | BNB Chain |
| **Price** | $0.1147 |
| **24h Volume** | $34.8K |
| **Liquidity** | $64.6K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 5d |
| **Top-10 Holders** | 76.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 812 buys / 511 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x3079ae2e87dc2e0c75c9b98d65bc622ad10f326c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/shopinx-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
