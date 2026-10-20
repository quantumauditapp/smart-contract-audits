---
token: BTN
ticker: BTN
network: base
risk_score: 22
status: low
date: 2026-10-13
---

# BTN (BTN) — Smart Contract Security Analysis | Base

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/btn-base)

---

## Audit Summary

The BTN contract is a standard ERC-20 token implementation. A key security posture is the renounced ownership, which renders all owner-restricted functions, including the `mint` function, permanently inactive. This significantly mitigates potential risks associated with privileged control over token supply. The audit identified one informational finding related to the dormant minting capability.

> **Final Recommendation:** For token holders, the renounced ownership provides a high degree of certainty that no central entity can manipulate the token supply or other owner-restricted parameters. It is crucial to understand that the contract's logic is immutable. Any future changes or fixes would require a new contract deployment and migration. Users should always verify the contract's address and ensure they are interacting with the intended, immutable version.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The BTN token is a standard ERC-20 implementation, providing core functionalities like transfer, approve, and balanceOf. The contract includes a `mint` function, which could increase the total supply… |
| **Governance / Economics** | 6/10 | Medium | The primary economic mechanism is the ERC-20 token standard. The contract initially had a `mint` function allowing the owner to increase token supply, which could lead to dilution (7.4 Economic).… |
| **Upgrades** | 6/10 | Medium | The BTN contract is not designed as an upgradeable proxy (7.7 Upgrades). This means its logic is immutable and cannot be changed or updated after deployment. This provides certainty regarding the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 80.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a wallet, 0x0d13…7d17 — holds 80.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Potential Token Dilution (Dormant)  *(Severity: Informational · Status: Unresolved)*

The BTN token contract contains a `mint(address,uint256)` function. If this function were active, the contract owner could create new BTN tokens, increasing the total supply. This action would dilute the value of existing BTN tokens held by users. However, the contract's ownership has been permanently renounced, meaning no one, including the original deployer, can call this `mint` function or any other owner-restricted functions.

**Recommendation:** As ownership is renounced, the `mint` function is permanently inactive, and there is no longer a risk of token dilution from this specific mechanism. Token holders do not need to take any action regarding this dormant capability. This status provides assurance that the token supply cannot be arbitrarily increased by a central party.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 98.7% of supply. Of that, 0.8% locked, 0.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.9% in wallets, 96.4% in other contracts. 1,994 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,994 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $101K (DexScreener, all pools). 24h trading volume $89K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $101K of DEX liquidity across 4 pools. Launch: 135 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6c41...fcf3`](https://basescan.org/address/0x6c417845facc97ebce84fbfee9a7460b0e5cfcf3) |
| **Network** | Base |
| **Price** | $0.4483 |
| **24h Volume** | $88.6K |
| **Liquidity** | $101.3K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 98.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 644 buys / 277 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xc069bb46ba971c3bf5424fb505525db3006d8091)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/btn-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-13*
