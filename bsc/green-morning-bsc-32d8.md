---
token: GREEN MORNING
ticker: GM
network: bsc
risk_score: 82
status: high
date: 2026-11-07
---

# GREEN MORNING (GM) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 82/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/green-morning-bsc-32d8)

---

## Audit Summary

The protocol implements a complex tax and liquidity management system via a UUPS proxy. While ownership has been renounced, several administrative functions remain accessible to specific roles or the contract itself, creating centralized control points. The architecture relies on automated marketing and liquidity processing, which introduces risks regarding fund management and potential slippage.

> **Final Recommendation:** Investors should monitor the 'idcollection' role and the contract's internal state, as these entities retain significant control over the token's economic parameters. Ensure that any future interactions with the protocol are performed through the official interface to avoid potential slippage or unexpected tax behavior.

Developers should consider implementing a time-lock for any future administrative changes if the ownership structure is ever restored. Additionally, ensure that the 'claimMarketing' function is strictly audited to prevent unauthorized access to accumulated ETH.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | The contract utilizes a UUPS proxy pattern to manage complex tax logic and automated liquidity provisioning. 7.1 Architecture is modular, separating tax state from core ERC-20 logic. 7.2 Code… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance aspects are heavily influenced by the 'idcollection' role and internal contract logic. While ownership is renounced, the ability for the contract to self-trigger… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are handled via the UUPS pattern, which is a standard and secure approach for upgradeable contracts. 7.8 Operations are currently restricted as ownership is renounced, limiting the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.8% (≈ permanent lock) |
| **LP Locked** | 99.8% — Null Address |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 2 Low · ⚪ 6 Informational_

### `CD-01` — Arbitrary ETH Transfer Risk  *(Severity: High · Status: Unresolved)*

The 'claimMarketing' function allows for the transfer of ETH to arbitrary addresses, which could be exploited if access control is bypassed or misconfigured.

**Recommendation:** Restrict ETH withdrawals to a pre-defined, immutable marketing wallet address.


### `CP-05` — Privileged Control Over Transfer Functionality  *(Severity: Medium · Status: Unresolved)*

A privileged address or the contract itself controls a switch that determines if transfers or sales are permitted. This allows the controller to halt trading or restrict specific wallet activities at will.

**Recommendation:** Implement a decentralized governance mechanism or a time-lock to prevent sudden, unilateral changes to trading status.


### `CP-07` — Dynamic Transfer Fee Manipulation  *(Severity: Medium · Status: Unresolved)*

The tax fees applied to token transfers can be modified by privileged roles. This creates a risk where fees could be adjusted to extract value from users unexpectedly.

**Recommendation:** Set hard caps on the maximum possible tax fees to protect users from excessive charges.


### `CD-02` — Rounding Loss via Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

The 'priceAt' function performs division before multiplication, which can lead to precision loss and inaccurate price calculations.

**Recommendation:** Reorder operations to perform multiplication before division to maintain precision.


### `CP-08` — Administrative Control Over Transaction Limits  *(Severity: Low · Status: Unresolved)*

Privileged addresses can modify transaction and wallet limits, potentially impacting liquidity and user accessibility.

**Recommendation:** Document these limits clearly in the UI and provide notice before any changes are applied.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 40.3% of supply. Of that, 29.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.7% in wallets, 0.7% in other contracts. 2,221 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,221 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.8% of the pool's LP is burned or time-locked. 99.8% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.2% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $23K (DexScreener, all pools). 24h trading volume $414K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $23K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf8fb...1ec7`](https://bscscan.com/address/0xf8fb136143e40d1dec963d5234fb7efce8b01ec7) |
| **Network** | BNB Chain |
| **Price** | $0.00000002 |
| **24h Volume** | $414.5K |
| **Liquidity** | $23.1K |
| **Volume / Liquidity** | 17.9× |
| **Token Age** | 1d |
| **Top-10 Holders** | 40.3% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 4484 buys / 5641 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xee5f1330424ebd075d3447efc972d04844b04f26)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/green-morning-bsc-32d8)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
