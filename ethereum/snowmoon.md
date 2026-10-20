---
token: snowmoon
ticker: SNOWMOON
network: ethereum
risk_score: 69
status: high
date: 2026-09-30
---

# snowmoon (SNOWMOON) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 69/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/snowmoon-eth)

---

## Audit Summary

The LaunchToken is an ERC-20 token deployed as an EIP-1167 minimal clone, making it non-upgradeable. While this provides stability regarding contract logic, several functions are controlled by privileged addresses (factory, rewardsource). These functions allow for minting new tokens, altering transfer fees, and changing transfer limits, which could impact token holders.

> **Final Recommendation:** It is crucial to establish robust operational security practices for the addresses holding privileged roles, such as the `factory` and `rewardSource`. Implement multi-signature wallets or time-locks for these roles to mitigate the risk of unauthorized or malicious actions. Ensure transparent communication with token holders regarding any changes to transfer fees or token supply that may occur through these privileged functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The LaunchToken implements the ERC-20 standard, providing basic token functionalities. Its architecture utilizes an EIP-1167 minimal clone pattern, ensuring the contract's logic is immutable… |
| **Governance / Economics** | 3/10 | High | The economic stability of the LaunchToken is influenced by several privileged functions. The `initialize` function allows a designated address to mint the initial token supply, which, if called… |
| **Upgrades** | 3/10 | High | The LaunchToken is deployed as an EIP-1167 minimal clone, which means its implementation is fixed and cannot be upgraded (7.7 Upgrades). This design choice eliminates risks associated with… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `CP-01` — Controller can create new tokens  *(Severity: Medium · Status: Unresolved)*

The `initialize` function allows the contract's controller (the address that deploys the clone) to create the initial total supply of tokens. While this is part of the setup, if this function were callable again or by another unauthorized address, it could create more tokens, diluting the value of existing tokens.

**Recommendation:** Ensure the `initialize` function is called only once and by the intended deployer. The current code prevents re-initialization by checking `factory != address(0)`. The risk lies in the initial setup and the power of the initial deployer.


### `CP-07` — Controller can change token transfer fees  *(Severity: Medium · Status: Unresolved)*

The `notifyReward` and `setMarket` functions, which can be called by the `factory` or `rewardSource` addresses, have the ability to change how transfer fees are calculated and applied. This means that the cost associated with sending or receiving tokens could be altered at any time by these privileged addresses.

**Recommendation:** Token holders should be aware that the `factory` and `rewardSource` addresses have the power to adjust transfer fees. Transparency from the project team regarding any fee changes is essential. Consider implementing a governance mechanism or a time-lock for such critical changes.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x449a…c0dd — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 89% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-08` — Controller can change transfer rules  *(Severity: Low · Status: Unresolved)*

The `initialize` function, callable by the contract's deployer, sets parameters like `_launchBlock` and `_rewardDebt` which influence transfer rules and amounts. While these are typically set once during deployment, the ability to define these initial conditions gives significant control over how transfers behave from the outset.

**Recommendation:** The `initialize` function is designed for initial setup. Ensure that the parameters set during initialization are carefully chosen and communicated to token holders, as they define fundamental aspects of the token's transfer mechanics.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 34.2% of supply. Of that, 4.0% burned — not holders that can sell, so excluded from the concentration score. What remains: 5.5% in wallets, 24.7% in other contracts. 1,193 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,193 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $85K (DexScreener, all pools). 24h trading volume $244K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (moon). Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $85K of DEX liquidity across 10 pools. Launch: 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbb39...9844`](https://etherscan.io/address/0xbb399b4a6557d44d58c626bce5346ad2f8fe9844) |
| **Network** | Ethereum |
| **Price** | $0.0002526 |
| **24h Volume** | $237.6K |
| **Liquidity** | $75.9K |
| **Volume / Liquidity** | 3.1× |
| **Token Age** | 2d |
| **Top-10 Holders** | 34.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 420 buys / 383 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x2f8e36dfd07aefa54876d4b2635dce86ba8c3503cb633f21ae1ee4c1d31b81ad)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/snowmoon-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-30*
