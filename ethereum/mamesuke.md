---
token: Mamesuke
ticker: MAMESUKE
network: ethereum
risk_score: 78
status: high
date: 2026-11-02
---

# Mamesuke (MAMESUKE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 78/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mamesuke-eth)

---

## Audit Summary

The Mamesuke contract is an ERC-20 token with centralized administrative controls. While ownership has been renounced, the 'mamwallet' address retains significant power to manipulate token balances and transfer rules. The protocol exhibits high centralization risk due to these privileged functions.

> **Final Recommendation:** The protocol should transition to a decentralized model by removing the 'mamwallet' privileges. The 'stakeProcess' function should be audited for potential abuse, as it allows arbitrary balance manipulation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements standard ERC-20 functionality with additional administrative hooks. 7.1 Architecture is straightforward, though 7.2 Code Security is impacted by reliance on block-based… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance are heavily centralized under the 'mamwallet'. The ability to move user balances via 'stakeProcess' presents a significant risk to token holders. There are no… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are managed via static administrative functions. No upgrade path exists for the current implementation. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 2 High · 🟡 2 Medium · 🟢 2 Low · ⚪ 5 Informational_

### `CD-02` — Predictable Randomness in Distribution  *(Severity: High · Status: Unresolved)*

The 'stakeProcess' function uses 'blockhash' for randomness, which is predictable by miners and can be manipulated to influence the distribution amounts.

**Recommendation:** Use a verifiable source of randomness like Chainlink VRF instead of block-based data.


### `CP-02` — Privileged Balance Manipulation  *(Severity: High · Status: Unresolved)*

The 'stakeProcess' function allows the 'mamwallet' to move tokens out of the contract to arbitrary addresses, effectively allowing the controller to distribute tokens at will.

**Recommendation:** Remove the ability for the 'mamwallet' to arbitrarily move tokens or restrict it to a transparent, community-governed process.


### `CP-05` — Centralized Control Over Transfers  *(Severity: Medium · Status: Unresolved)*

The 'mamwallet' can toggle the 'clogsEnabled' switch and trigger swaps, which can halt or restrict user transfers at any time.

**Recommendation:** Implement a time-lock or multi-sig requirement for administrative actions that affect user transfers.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $10K (DexScreener, all pools). 24h trading volume $32K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `CD-01` — Rounding Loss in Calculations  *(Severity: Low · Status: Unresolved)*

The 'stakeProcess' function performs division before multiplication, which can lead to precision loss in token distribution.

**Recommendation:** Perform all multiplications before divisions to maintain precision.


### `CP-08` — Administrative Control Over Limits  *(Severity: Low · Status: Unresolved)*

The 'mamwallet' can modify transaction and wallet limits, potentially creating unfair trading conditions.

**Recommendation:** Hardcode limits or use a decentralized governance vote to adjust them.


### `CP-07` — Dormant Administrative Functions  *(Severity: Informational · Status: Unresolved)*

Functions like 'updatemamTaxRates' are restricted to the owner, but ownership has been renounced, rendering these functions permanently unusable.

**Recommendation:** Remove these functions during the next deployment to clean up the contract code.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 96.9% of supply. Of that, 70.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 13.8% in wallets, 12.8% in other contracts. 114 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

114 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10K of DEX liquidity across 2 pools. Launch: 210 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2e1f...324b`](https://etherscan.io/address/0x2e1f4d0cc87a195957d1dd8e663451147db3324b) |
| **Network** | Ethereum |
| **Price** | $0. |
| **24h Volume** | $32.0K |
| **Liquidity** | $9.4K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 96.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 178 buys / 117 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xec6272f2d4e55b01936b1e2ba18a82088540531f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mamesuke-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
