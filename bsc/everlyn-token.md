---
token: Everlyn Token
ticker: LYN
network: bsc
risk_score: 19
status: low
date: 2026-10-09
---

# Everlyn Token (LYN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/everlyn-token-bsc)

---

## Audit Summary

The EverlynToken contract is a standard ERC-20 token implementation. Its ownership has been renounced on-chain, which means no single entity can control critical token parameters or execute privileged functions. A potential minting capability exists but is currently dormant due to the renounced ownership, ensuring a fixed total supply.

> **Final Recommendation:** For token holders, the renounced ownership provides a high degree of certainty regarding the immutability of the token's core parameters, including its supply. It is recommended to always verify the ownership status of contracts and understand the implications of renounced ownership. For future projects, consider the trade-offs between upgradeability and immutability based on project requirements and long-term vision.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The EverlynToken contract implements the ERC-20 standard, providing basic token functionalities like transfer and approval. The contract's ownership has been renounced on-chain, which means functions… |
| **Governance / Economics** | 7/10 | Low | The economic model is based on a standard ERC-20 token. While a `mint` function exists, its associated risk of token dilution (7.4 Economic) is mitigated because ownership has been renounced. This… |
| **Upgrades** | 6/10 | Medium | The EverlynToken contract is a standard implementation and does not utilize any proxy patterns (7.7 Upgrades). Therefore, it is not upgradeable, meaning its logic cannot be changed after deployment.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 50.6% |
| **Top-3 Unlocked** | 63.2% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 85.9% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a wallet, 0xc055…9d4a — holds 50.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 81% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — A privileged address can mint new tokens  *(Severity: Informational · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Ownership is renounced, so no one can call these functions now. Functions: mint(address,uint256). Restricted to: owner.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 92.4% of supply. What remains: 18.2% in wallets, 74.2% in other contracts. 21,977 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Everlyn (LYN), market cap $4M, rank #1935. 21,977 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $65K (DexScreener, all pools). 24h trading volume $2.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $302K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.605 on 2025-10-05; the price is now 97.1304% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $65K of DEX liquidity across 3 pools. Launch: 368 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x302d...877d`](https://bscscan.com/address/0x302dfaf2cdbe51a18d97186a7384e87cf599877d) |
| **Network** | BNB Chain |
| **Price** | $0.01701 |
| **24h Volume** | $293.3K |
| **Liquidity** | $52.8K |
| **Volume / Liquidity** | 5.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 92.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1849 buys / 1974 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x302642976506d247c7017b85ddc89e3956f96ba1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/everlyn-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*
