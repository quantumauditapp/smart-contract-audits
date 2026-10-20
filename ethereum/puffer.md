---
token: Puffer
ticker: PUFFER
network: ethereum
risk_score: 50
status: medium
date: 2026-10-15
---

# Puffer (PUFFER) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/puffer-eth)

---

## Audit Summary

The PUFFER contract is an ERC-20 token with voting capabilities. Its ownership has been renounced, meaning no single entity can control the contract's privileged functions, including those that could pause transfers or set address-specific transfer rules. One informational finding was identified regarding dormant pause functionality, which poses no active risk due to the renounced ownership.

> **Final Recommendation:** Token holders should be aware that the contract's ownership has been renounced, meaning no single entity can modify its core parameters or privileged functions. This provides a high degree of immutability and reduces central point of failure risks. Users should always verify the contract address and understand the token's specific functionalities before interacting with it.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The PUFFER contract implements standard ERC-20 token functionality (7.1 Architecture), including `transfer`, `transferFrom`, and `approve`. It also includes ERC20Permit and ERC20Votes for off-chain… |
| **Governance / Economics** | 6/10 | Medium | The contract incorporates ERC20Votes, enabling token holders to delegate voting power and participate in governance (7.5 Governance). However, with renounced ownership, there are no active… |
| **Upgrades** | 8/10 | Low | The PUFFER contract is not implemented as a proxy (7.7 Upgrades) and therefore does not support upgradeability. This eliminates any risks associated with upgrade mechanisms, such as malicious upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 81.1% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x495a…a1a2 — holds 81.1% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 56% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-04` — A privileged address can pause transfers  *(Severity: Informational · Status: Unresolved)*

A privileged switch checked on every transfer can stop all transfers. Ownership is renounced, so no one can call these functions now. Functions: unpause. Restricted to: owner.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 70.4% of supply. What remains: 27.3% in wallets, 43.1% in other contracts. 25,984 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Puffer (PUFFER), market cap $15M, rank #996. 25,984 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $433K (DexScreener, all pools). 24h trading volume $6.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.8M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.991 on 2024-12-07; the price is now 97.45% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Liquid Restaking Governance Tokens. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $433K of DEX liquidity across 5 pools. Launch: 730 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4d1c...4530`](https://etherscan.io/address/0x4d1c297d39c5c1277964d0e3f8aa901493664530) |
| **Network** | Ethereum |
| **Price** | $0.05413 |
| **24h Volume** | $747.9K |
| **Liquidity** | $241.6K |
| **Volume / Liquidity** | 3.1× |
| **Token Age** | 2y |
| **Top-10 Holders** | 70.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 536 buys / 450 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xc5c9a9ab6403cdba9722463000146c18b504f0ba)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/puffer-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
