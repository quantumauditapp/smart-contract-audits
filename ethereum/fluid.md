---
token: Fluid
ticker: FLUID
network: ethereum
risk_score: 36
status: medium
date: 2026-10-06
---

# Fluid (FLUID) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fluid-eth)

---

## Audit Summary

The InstaToken contract, serving as a proxy implementation, exhibits centralized control over core token functionalities. A single privileged address (`instaindex`) can mint new tokens, thereby diluting existing holders, and can pause/unpause all token transfers, potentially freezing user assets. While standard ERC-20 functions are present, these centralized powers introduce significant governance and economic risks.

> **Final Recommendation:** It is strongly recommended to enhance decentralization and transparency for all critical functions. Implementing multi-signature wallets or time-locks for privileged actions such as token minting, pausing transfers, and contract upgrades would significantly reduce single points of failure and increase community trust. Furthermore, clear documentation of the upgrade process and the governance structure surrounding it is essential to ensure token holders understand how future changes will be managed and approved.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract implements standard ERC-20 functionalities like `transfer` and `transferFrom`, utilizing `safe96` for amount handling to mitigate overflow/underflow for 96-bit values (7.2 Code… |
| **Governance / Economics** | 1/10 | High | The token's economic model and governance are highly centralized, posing significant risks (7.4 Economic, 7.5 Governance). A single `instaindex` address holds extensive power, including the ability… |
| **Upgrades** | 1/10 | High | The contract is identified as a proxy implementation (`InstaTokenDelegate`) for `InstaToken`, enabling future logic upgrades (7.1 Architecture, 7.7 Upgrades). This flexibility allows for bug fixes… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 97.9% |
| **Top-3 Unlocked** | ⚠️ 99.9% |

## Security Findings

_🟡 3 Medium · ⚪ 4 Informational_

### `CP-01` — A privileged address can mint new tokens  *(Severity: Medium · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: mint(address,uint256). Restricted to: instaindex.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `CP-04` — A privileged address can pause transfers  *(Severity: Medium · Status: Unresolved)*

A privileged switch checked on every transfer can stop all transfers. Functions: pauseTransfer, unpauseTransfer. Restricted to: instaindex.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a contract, 0xe875…e34f — holds 97.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 89% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 56.1% of supply. What remains: 0.0% in wallets, 56.1% in other contracts. 11,827 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Fluid (FLUID), market cap $163M, rank #214. 11,827 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $5.2M (DexScreener, all pools). 24h trading volume $19.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.5M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $24.40 on 2021-06-16; the price is now 92.0238% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: vote delegation in its code. Tokenomics — Supply: mintable, capped at 2.0% of supply per year. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $5.2M of DEX liquidity across 9 pools. Launch: 1940 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6f40...03eb`](https://etherscan.io/address/0x6f40d4a6237c257fff2db00fa0510deeecd303eb) |
| **Network** | Ethereum |
| **Price** | $2.0220 |
| **24h Volume** | $748.3K |
| **Liquidity** | $4.60M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 5y |
| **Top-10 Holders** | 56.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 224 buys / 233 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xc1cd3d0913f4633b43fcddbcd7342bc9b71c676f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fluid-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
