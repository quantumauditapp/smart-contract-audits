---
token: Woof
ticker: WOOF
network: ethereum
risk_score: 76
status: high
date: 2026-09-29
---

# Woof (WOOF) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 76/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/woof-eth)

---

## Audit Summary

The LaunchToken contract is an ERC-20 token designed for a launchpad system, deployed as a minimal clone. The audit identified medium-level risks related to privileged control over token supply, transfer fees, and transfer limits. The 'factory' and 'rewardSource' roles have significant power, including the ability to mint new tokens and modify economic parameters post-deployment. While the contract uses a minimal clone proxy, the implementation itself is not designed for upgrades, simplifying upgrade safety.

> **Final Recommendation:** It is crucial to ensure that the private keys controlling the 'factory' and 'rewardSource' addresses are secured with multi-signature wallets or robust access control mechanisms. Token holders should be fully aware of the extent of control these privileged roles possess over token supply, transfer fees, and other economic parameters. Consider implementing a timelock for critical parameter changes to provide transparency and allow community review.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The LaunchToken contract implements the ERC-20 standard with additional privileged functions (7.1 Architecture). Key functions like `initialize`, `setMarket`, and `notifyReward` are restricted to… |
| **Governance / Economics** | 2/10 | High | The economic model (7.4 Economic) of the LaunchToken is heavily influenced by privileged roles. The `factory` can mint new tokens via `initialize`, potentially diluting existing token holders.… |
| **Upgrades** | 3/10 | High | The contract is deployed as a minimal clone (7.7 Upgrades), meaning each deployed instance is a fixed copy of the implementation and is not directly upgradeable. The `initialize` function serves as a… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `CP-01` — Privileged Address Can Mint New Tokens  *(Severity: Medium · Status: Unresolved)*

The `initialize` function allows the 'factory' address to mint the entire `TOTAL_SUPPLY` of tokens. This means that if the 'factory' address is compromised or acts maliciously, it could mint additional tokens beyond the initial supply, diluting the value for all existing token holders.

**Recommendation:** Token holders should be aware that the 'factory' address has the power to mint the initial token supply. While this is a one-time operation during initialization, any subsequent unauthorized minting by a compromised 'factory' address would dilute their holdings. Ensure the 'factory' address is highly secured.


### `CP-07` — Privileged Address Can Change Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The `notifyReward` and `setMarket` functions, callable by the 'factory' or 'rewardSource' addresses, can change parameters that influence transfer fees, such as `accRewardPerToken` and `eligibleSupply`. This means that the controllers of these addresses can unilaterally modify the fees applied to token transfers, potentially impacting the cost of transactions for token holders.

**Recommendation:** Token holders should understand that the 'factory' and 'rewardSource' addresses have the ability to adjust transfer fees. This could affect the economics of holding and transferring the token. It is important that these addresses are controlled by trusted entities and that any changes are communicated transparently.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xc796…6c47 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 94% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-08` — Privileged Address Can Change Transfer or Wallet Limits  *(Severity: Low · Status: Unresolved)*

The `initialize` function, callable by the 'factory' address, sets the `_launchBlock` parameter. This parameter is used in transfer rules and could potentially affect transfer or wallet limits, such as restrictions on transfers before a certain block number. A malicious or compromised 'factory' could manipulate this to impose unexpected restrictions on token transfers.

**Recommendation:** Token holders should be aware that the 'factory' address sets initial parameters like `_launchBlock` during initialization, which can influence transfer rules. While this is a one-time setup, it's important to trust the entity controlling the 'factory' to set these parameters fairly, as they could affect when and how tokens can be transferred.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 88.4% of supply. What remains: 5.0% in wallets, 83.4% in other contracts. 136 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

136 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $183K (DexScreener, all pools). 24h trading volume $1.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $183K of DEX liquidity across 11 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa912...8eae`](https://etherscan.io/address/0xa912c71c0e53701153cad9ba73e9b7d854418eae) |
| **Network** | Ethereum |
| **Price** | $0.001048 |
| **24h Volume** | $1.52M |
| **Liquidity** | $172.8K |
| **Volume / Liquidity** | 8.8× |
| **Token Age** | 23h |
| **Top-10 Holders** | 88.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2600 buys / 1857 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x0be16b24f634f1de1d529d44fc3e284462da11800613ceea662a70d6e57e258c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/woof-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-29*
