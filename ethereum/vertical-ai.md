---
token: Vertical AI
ticker: VERTAI
network: ethereum
risk_score: 64
status: medium
date: 2026-10-03
---

# Vertical AI (VERTAI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vertical-ai-eth)

---

## Audit Summary

The VerticalAI contract is an ERC-20 token with several owner-controlled parameters. The audit identified significant centralization risks due to the owner's ability to modify core token behaviors such as fee receivers, swapping functionality, transfer fees, and wallet/swap limits. These controls grant the owner substantial power over the token's operation and economic model.

> **Final Recommendation:** It is strongly recommended to decentralize control over critical parameters where possible, or to implement multi-signature wallets for owner functions to reduce single points of failure. Clear documentation of all owner-controlled functions and their potential impact should be provided to token holders to ensure transparency. Consider implementing time-locks for sensitive changes to allow community review and reaction time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The VerticalAI contract implements the ERC-20 standard, providing standard token functionalities like transfer and approval. The contract includes several owner-restricted functions that directly… |
| **Governance / Economics** | 4/10 | Medium | The economic model of the VerticalAI token is heavily reliant on owner control. The owner can adjust the `marketingFee` via `lowerFees` and set `maxWalletSize` and `maxSwapThreshold` using… |
| **Upgrades** | 7/10 | Low | The VerticalAI contract is not implemented as an upgradeable proxy (7.7 Upgrades). Therefore, there are no upgrade-related risks such as proxy misconfigurations or logic contract vulnerabilities… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — UNCX Locker |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `CP-03` — Owner Can Redirect Token Fees  *(Severity: High · Status: Unresolved)*

The owner of the VerticalAI token can change the address that receives marketing fees by calling the `changeFeeReceiver` function. This means the owner could redirect all accumulated marketing fees to an address they control, potentially draining funds intended for the project's development or ecosystem.

**Recommendation:** Token holders should be aware that the owner has the power to redirect the destination of marketing fees. This introduces a centralization risk where the owner could potentially divert funds. Consider implementing a multi-signature wallet or a time-lock for such critical changes.


### `CP-05` — Owner Can Halt Token Swapping  *(Severity: Medium · Status: Unresolved)*

The owner can enable or disable token swapping functionality using the `toggleSwapping` function. If swapping is disabled, users might be unable to sell or transfer their tokens, effectively freezing liquidity or preventing market activity, which could severely impact token utility.

**Recommendation:** Token holders should understand that the owner possesses the ability to stop all token swapping. This could severely impact liquidity and the ability to trade tokens. It is recommended to remove or decentralize this control, or at least implement a time-lock.


### `CP-07` — Owner Can Adjust Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The owner can modify the `marketingFee` applied to token transfers using the `lowerFees` function. While the current function only allows lowering fees, the existence of such a control point indicates the owner's ability to influence transaction costs and the token's economic model.

**Recommendation:** Token holders should be aware that the owner can change the fees associated with token transfers. While currently restricted to lowering fees, this control point represents a centralized influence on the token's economic model. Future changes could potentially allow raising fees, which should be considered.


### `CP-08` — Owner Can Modify Transfer and Wallet Limits  *(Severity: Low · Status: Unresolved)*

The owner can adjust various limits affecting token transfers and wallet holdings. Specifically, the `raiseMaxLimit` function can increase the maximum wallet size, and `setSwapThreshold` can change the threshold for swaps. These controls allow the owner to influence how much token can be held or swapped, potentially affecting market dynamics and individual user capabilities.

**Recommendation:** Token holders should note that the owner can change limits on wallet holdings and swap thresholds. This means the owner can dictate how much token an individual address can hold or how much can be swapped at once, potentially affecting market dynamics. Transparency regarding these limits and changes is crucial.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 47.1% of supply. Of that, 2.0% burned, 5.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 3.9% in wallets, 36.2% in other contracts. 11,199 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Vertical AI (VERTAI), market cap $2M, rank #2572. 11,199 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked, lock term not visible  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is held by UNCX Locker, but the lock's end date is not published in the data we can read — its duration is unverified. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $198K (DexScreener, all pools). 24h trading volume $55K (CoinGecko, all markets, daily snapshot). 24h trading volume $49K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1.14 on 2025-01-04; the price is now 98.2249% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $198K of DEX liquidity across 2 pools. Launch: 612 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcdbd...d567`](https://etherscan.io/address/0xcdbddbdefb0ee3ef03a89afcd714aa4ef310d567) |
| **Network** | Ethereum |
| **Price** | $0.01943 |
| **24h Volume** | $49.2K |
| **Liquidity** | $196.1K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 47.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 87 buys / 105 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xbaa1fceff65e21d547bf6747b0b777a32be53668)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vertical-ai-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*
