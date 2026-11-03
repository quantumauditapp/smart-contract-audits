---
token: 零号病毒
ticker: 零号病毒
network: bsc
risk_score: 62
status: medium
date: 2026-11-03
---

# 零号病毒 (零号病毒) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-fd7f20-bsc)

---

## Audit Summary

The AI token is a standard ERC-20 implementation with custom minting logic and centralized control mechanisms. The contract allows for a 'minting' phase via the receive function, which is gated by privileged addresses. While the contract includes standard token functionality, the reliance on centralized control for transfer logic and minting parameters presents significant risks to token holders.

> **Final Recommendation:** It is recommended to implement a multi-signature wallet for all privileged functions to mitigate the risk of a single point of failure. Additionally, consider replacing the centralized control switches with a time-locked governance mechanism to provide transparency to token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows a standard ERC-20 pattern with added minting capabilities. 7.1 Architecture is straightforward, though 7.2 Code Security reveals issues with rounding and logic flow. 7.3… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are highly centralized. The owner can manipulate transfer rules and minting thresholds at will, which directly impacts token liquidity and holder value. There… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are limited to the owner's ability to renounce ownership or trigger the launch function. Once ownership is renounced, the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 99.9% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 0.1% |

## Security Findings

_🟡 3 Medium · 🟢 2 Low · ⚪ 5 Informational_

### `CD-01` — Boolean Logic Complexity  *(Severity: Medium · Status: Unresolved)*

The _transfer function contains complex boolean logic that may lead to unexpected behavior during token transfers.

**Recommendation:** Simplify the transfer logic to improve readability and reduce the likelihood of logic errors.


### `CP-05` — Centralized Control over Transfers  *(Severity: Medium · Status: Unresolved)*

A privileged address can toggle a switch that determines whether transfers are permitted. This allows the controller to effectively freeze or unfreeze token trading at their discretion.

**Recommendation:** Remove the centralized switch or implement a decentralized voting mechanism to govern trading pauses.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $10K (DexScreener, all pools). 24h trading volume $119K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `CD-02` — Rounding Loss in Calculations  *(Severity: Low · Status: Unresolved)*

The swapTokenForFund function performs division before multiplication, which can lead to precision loss and inaccurate fee calculations.

**Recommendation:** Perform all multiplications before divisions to maintain precision.


### `CP-08` — Centralized Control over Limits  *(Severity: Low · Status: Unresolved)*

The owner or privileged addresses can modify transaction and wallet limits. This allows for arbitrary changes to the economic constraints of the token.

**Recommendation:** Hardcode limits or use a community-governed parameter update process.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 50.7% of supply. Of that, 2.2% burned, 26.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 14.3% in wallets, 7.6% in other contracts. The deployer/owner wallet itself holds 2.2%. 56,508 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

56,508 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

99.9% of the pool's LP is burned or time-locked. 99.9% is locked in PinkLock02 until 01 Jan 2028 (424 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: 2% on buy, 2.03% on sell. Market: $10K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe878...8216`](https://bscscan.com/address/0xe878412bfcaafbb3551f70098f765a9c09da8216) |
| **Network** | BNB Chain |
| **Price** | $0. |
| **24h Volume** | $118.7K |
| **Liquidity** | $9.8K |
| **Volume / Liquidity** | 12.1× |
| **Token Age** | 22h |
| **Top-10 Holders** | 50.7% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 2718 buys / 2830 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xf2c9f18dacf05538ebc5437d7b7592c0d37d5dc1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-fd7f20-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
