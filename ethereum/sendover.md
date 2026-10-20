---
token: Sendover
ticker: SENDOVER
network: ethereum
risk_score: 75
status: high
date: 2026-10-10
---

# Sendover (SENDOVER) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sendover-eth)

---

## Audit Summary

The LaunchToken contract is an ERC-20 token implemented as an EIP-1167 minimal clone. It features specific mechanisms for managing rewards and transfer rules. The audit identified several areas where privileged addresses (factory, rewardsource) have significant control, including the ability to mint new tokens, modify transfer fees, and influence transfer rules. The contract is not upgradeable, which eliminates upgrade-related risks but also prevents future bug fixes or feature enhancements without a new deployment.

> **Final Recommendation:** For token holders, it is crucial to understand the extent of control held by the `factory` and `rewardsource` addresses over the LaunchToken's economic parameters. Monitor official communications for any changes to transfer fees or other operational rules. Given the non-upgradeable nature of the contract, ensure thorough due diligence on the initial deployment and the trustworthiness of the controlling entities, as no future code modifications are possible.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The LaunchToken is an ERC-20 compliant token deployed as an EIP-1167 minimal clone, ensuring its logic is fixed and non-upgradeable (7.1 Architecture). The contract includes standard ERC-20… |
| **Governance / Economics** | 1/10 | High | The economic model of LaunchToken grants significant control to privileged addresses, primarily the `factory` and `rewardsource` (7.4 Economic). The `initialize` function allows the `factory` to mint… |
| **Upgrades** | 2/10 | High | The LaunchToken contract is deployed as an EIP-1167 minimal clone, meaning its implementation is fixed at deployment and cannot be upgraded (7.7 Upgrades). This design choice eliminates all… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `CP-01` — A privileged address can mint new tokens  *(Severity: Medium · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: initialize(string,string,string,address).

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `CP-07` — A privileged address can change the transfer fee  *(Severity: Medium · Status: Unresolved)*

The fee taken from transfers is a setting a privileged function can change. Functions: notifyReward, initialize, setMarket. Restricted to: factory, rewardsource.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x8448…b1a4 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-08` — A privileged address can change transfer or wallet limits  *(Severity: Low · Status: Unresolved)*

Numeric limits checked in the transfer path (maximum transaction or wallet size, thresholds) can be changed by a privileged function. Functions: initialize.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 32.4% of supply. What remains: 11.6% in wallets, 20.8% in other contracts. 294 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Sendover (SENDOVER), rank #4971. 294 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $64K (DexScreener, all pools). 24h trading volume $30K (CoinGecko, all markets, daily snapshot). 24h trading volume $31K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $64K of DEX liquidity across 2 pools. Launch: 15 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 15 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 15 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9925...9176`](https://etherscan.io/address/0x9925805b9b0dda34418798ccf95bcff5633f9176) |
| **Network** | Ethereum |
| **Price** | $0.0001907 |
| **24h Volume** | $30.7K |
| **Liquidity** | $63.6K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 15d |
| **Top-10 Holders** | 32.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 106 buys / 69 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xd668b057fe16d607576d3f0ed837ad959956701158d803e670f434c66dcfb961)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sendover-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
