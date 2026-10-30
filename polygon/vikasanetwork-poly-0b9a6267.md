---
token: Vikasa Network
ticker: VIK
network: polygon
risk_score: 71
status: high
date: 2026-10-29
---

# Vikasa Network (VIK) — Smart Contract Security Analysis | Polygon

> **Risk Score: 71/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vikasanetwork-poly-0b9a6267)

---

## Audit Summary

VikasaNetwork is a standard ERC-20 token implementation deployed on the Polygon network. The contract utilizes OpenZeppelin's Ownable and ERC20 libraries, ensuring standard compliance and robust base logic. No critical vulnerabilities or backdoors were identified in the transfer path or administrative functions.

> **Final Recommendation:** The contract is secure and follows best practices for a standard ERC-20 token. No further code changes are required for security purposes.

Maintain secure custody of the private key associated with the contract owner address to prevent unauthorized ownership transfers or renouncement.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows industry-standard ERC-20 patterns using well-audited OpenZeppelin libraries. 7.1 Architecture is clean and modular, while 7.2 Code Security benefits from the use of Solidity… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance parameters are straightforward as the contract lacks complex staking or minting logic. The owner has no power to manipulate token balances or restrict transfers… |
| **Upgrades** | 5/10 | Medium | The contract is not upgradeable, which eliminates 7.7 Upgrades risk. 7.8 Operations are limited to ownership transfer, which is handled via standard secure patterns. No proxy patterns are utilized… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 4 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0xed28…c9ee) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 65% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $2K (GeckoTerminal, all pools). 24h trading volume $0 (GeckoTerminal, all pools). Almost nobody trades it: a sale of any size moves the price hard, if a buyer is there at all.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 99.7% locked — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 0.2% in other contracts. 15 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

15 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $2K of DEX liquidity across 3 pools. Launch: 40 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2921...00c1`](https://polygonscan.com/address/0x2921d67ac78ebda0020f952e51e931ed125e00c1) |
| **Network** | Polygon |
| **Price** | $0.10298989 |
| **24h Volume** | N/A |
| **Liquidity** | $974 |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |

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

- [View on DexScreener](https://polygonscan.com/address/0x2921d67ac78ebda0020f952e51e931ed125e00c1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vikasanetwork-poly-0b9a6267)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
