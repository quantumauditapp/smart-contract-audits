---
token: VELLORA
ticker: VELL
network: bsc
risk_score: 30
status: low
date: 2026-10-08
---

# VELLORA (VELL) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 30/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vellora-bsc)

---

## Audit Summary

The VELLORA token contract is an ERC-20 implementation with integrated transfer fees and administrative controls. The audit identified a medium-severity issue related to the owner's ability to change transfer fees and a low-severity issue concerning potential rounding loss in internal calculations. The contract's architecture grants significant centralized control to the owner and marketing manager over key economic and operational parameters.

> **Final Recommendation:** The VELLORA token contract exhibits a high degree of centralized control, particularly over its economic parameters. The owner has the ability to unilaterally adjust transfer fees, manage fee exemptions, and control key operational addresses. Token holders should be fully aware of these centralized powers, as they introduce significant economic and governance risks.
It is strongly recommended to implement robust access control mechanisms, such as multi-signature wallets or timelocks, for critical functions like `setFees`, `setMarketingWallet`, and `setFeeExempt`. This would distribute control and introduce a delay for sensitive changes, allowing for community review and reducing the risk of malicious or erroneous actions. Additionally, all administrative actions should be transparently communicated to the community.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The VELLORA token implements standard ERC-20 functionality, including `transfer` and `transferFrom` methods. The contract incorporates a fee mechanism for transfers, which can be configured by… |
| **Governance / Economics** | 6/10 | Medium | The contract exhibits significant centralized control over economic parameters. The owner can set `buyFee`, `sellFee`, and `burnFee` using `setFees`, and also control `maxTotalFee` and… |
| **Upgrades** | 7/10 | Low | The VELLORA contract is not designed with an upgrade mechanism, as it is not deployed as a proxy (7.7 Upgrades). This means its logic is immutable once deployed. Any future changes or bug fixes would… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, PinkLock02 |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `CP-07` — Owner can change token transfer fees  *(Severity: Medium · Status: Unresolved)*

The owner of the VELLORA token contract has the ability to change the fees applied to token transfers. Specifically, the `setFees` function allows the owner to adjust the `buyFee`, `sellFee`, and `burnFee` that are deducted from transactions. This means the owner can unilaterally increase or decrease the cost of transacting with VELLORA tokens.

**Recommendation:** Token holders should be aware that the owner has significant control over the token's economic parameters. It is recommended that the project clearly communicate its policy regarding fee changes and consider implementing a timelock or multi-signature wallet for such critical functions to introduce a delay and require broader consensus.


### `CD-01` — Potential for minor rounding errors in calculations  *(Severity: Low · Status: Unresolved)*

The contract's internal calculations, specifically in the `slitherConstructorVariables` (likely related to initial state setup or internal constant calculations), might perform division before multiplication. This order of operations can lead to minor rounding losses, potentially resulting in slightly less precise outcomes for certain calculations.

**Recommendation:** While often minor, it's best practice to ensure calculations prioritize multiplication before division to maintain maximum precision. The project should review its internal arithmetic operations to prevent any potential rounding discrepancies, especially for sensitive financial calculations.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 61.3% of supply. Of that, 35.0% locked, 4.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.3% in wallets, 6.7% in other contracts. 2,744 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as VELLORA (VELL). 2,744 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 08 Oct 2027 (365 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $361K (DexScreener, all pools). 24h trading volume $56K (CoinGecko, all markets, daily snapshot). 24h trading volume $65K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $361K of DEX liquidity across 1 pools. Launch: 133 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x40f4...53f2`](https://bscscan.com/address/0x40f4100b47189c4b41b5ae3d3156d304b3f753f2) |
| **Network** | BNB Chain |
| **Price** | $0.008281 |
| **24h Volume** | $65.3K |
| **Liquidity** | $361.5K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 61.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 460 buys / 170 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xdbd63d58db817b3483f7e0f80e7239590e0ee115)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vellora-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
