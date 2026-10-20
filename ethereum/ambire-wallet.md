---
token: Ambire Wallet
ticker: WALLET
network: ethereum
risk_score: 53
status: medium
date: 2026-10-02
---

# Ambire Wallet (WALLET) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 53/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ambire-wallet-eth)

---

## Audit Summary

The WALLETToken contract implements basic ERC-20 functionalities with an additional minting capability controlled by a `supplycontroller` address. While core transfer mechanisms appear sound, the ability for a single entity to increase token supply introduces a centralized economic risk. One medium-severity finding related to this minting function was identified.

> **Final Recommendation:** Token holders should be fully aware of the centralized control over token supply. It is crucial to understand who holds the `supplycontroller` role and their policies regarding token minting. Projects should consider implementing a more decentralized governance model for critical functions like token minting, or at least provide transparency and clear communication channels regarding any planned supply changes. Regular monitoring of the `supplycontroller` address and its actions is advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The WALLETToken contract provides standard ERC-20 functionalities such as `transfer`, `transferFrom`, `approve`, `balanceOf`, and `allowance`. The implementation of these core functions (7.2 Code… |
| **Governance / Economics** | 1/10 | High | The economic model of WALLETToken is heavily influenced by the `supplycontroller` address, which has the sole authority to `mint` new tokens (7.4 Economic). This centralized control over the token… |
| **Upgrades** | 2/10 | High | The WALLETToken contract is not implemented as an upgradeable proxy (7.7 Upgrades). Therefore, the contract's logic cannot be modified or upgraded after deployment. This eliminates upgrade-related… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 72.8% |
| **Top-3 Unlocked** | ⚠️ 85.9% |

## Security Findings

_🟡 3 Medium · ⚪ 3 Informational_

### `CP-01` — Privileged Token Minting Capability  *(Severity: Medium · Status: Unresolved)*

The `supplycontroller` address has the ability to call the `mint(address,uint256)` function, which creates new tokens and adds them to the total supply. This means that the controller can increase the total number of tokens at any time, potentially diluting the value of existing tokens held by other users.

**Recommendation:** Token holders should be aware that the `supplycontroller` can mint new tokens. It is recommended to understand the project's policy regarding token supply increases and to monitor the `supplycontroller` address for any changes or unexpected minting activity. Consider if the project's governance model allows for community input on such critical actions.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 98.6% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a contract, 0x55e0…a4fa — holds 72.8% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $829K (DexScreener, all pools). 24h trading volume $273K (CoinGecko, all markets, daily snapshot). 24h trading volume $244K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $15.23 on 2026-05-13; the price is now 99.8833% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 79.2% of supply. Of that, 4.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 8.1% in wallets, 66.7% in other contracts. 9,016 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Ambire Wallet (WALLET), market cap $13M, rank #1139. 9,016 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: supplycontroller — a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $829K of DEX liquidity across 3 pools. Launch: 1706 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8880...94ae`](https://etherscan.io/address/0x88800092ff476844f74dc2fc427974bbee2794ae) |
| **Network** | Ethereum |
| **Price** | $0.01811 |
| **24h Volume** | $244.0K |
| **Liquidity** | $828.7K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 4y |
| **Top-10 Holders** | 79.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 123 buys / 85 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x53bbdf4ea397d17a6f904dc882b3fb78a6875a66)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ambire-wallet-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-02*
