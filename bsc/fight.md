---
token: FIGHT
ticker: FIGHT
network: bsc
risk_score: 61
status: medium
date: 2026-10-31
---

# FIGHT (FIGHT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 61/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fight-bsc)

---

## Audit Summary

The FightOFTSecondary contract is an Omnichain Fungible Token implementation on BSC. The architecture relies on LayerZero for cross-chain messaging. While the core ERC-20 logic is standard, the contract includes minting capabilities triggered by cross-chain messages, which introduces inherent risks regarding supply inflation and cross-chain security. 7.1 Architecture: Standard OFT implementation. 7.2 Code Security: Follows established patterns. 7.3 Access Control: Owner-restricted functions are protected. 7.4 Economic: Inflationary risk via cross-chain minting. 7.5 Governance: Centralized ownership. 7.6 External: Dependency on LayerZero endpoint. 7.7 Upgrades: Not upgradeable. 7.8 Operations: Standard.

> **Final Recommendation:** Implement a rate-limiting mechanism or a daily minting cap for cross-chain transfers to mitigate the impact of a potential LayerZero endpoint compromise. Ensure the multisig signers are geographically and organizationally distributed to maintain the integrity of the administrative functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a well-audited LayerZero OFT framework. Code quality is high, adhering to modern Solidity standards and gas-efficient patterns. The implementation correctly separates… |
| **Governance / Economics** | 1/10 | High | The protocol is governed by a 3-of-4 multisig, providing a reasonable balance of security and operational agility. The primary economic risk is the ability to mint tokens via cross-chain messages… |
| **Upgrades** | 3/10 | High | The contract is not upgradeable, which eliminates risks associated with proxy logic or malicious implementation swaps. This immutability ensures that the current logic remains consistent throughout… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Privileged Cross-Chain Minting Capability  *(Severity: Medium · Status: Unresolved)*

The functions send, lzReceiveSimulate, and lzReceive allow the contract to mint new tokens based on cross-chain messages. This increases the total supply and can dilute existing token holders if the cross-chain bridge or the LayerZero endpoint is compromised.

**Recommendation:** Implement a maximum minting cap per transaction or a time-based velocity limit to restrict the amount of tokens that can be minted via cross-chain operations.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x43f3…85a3 — holds 99.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 90% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 89.0% of supply. What remains: 35.7% in wallets, 53.3% in other contracts. 24,081 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as FIGHT (FIGHT), market cap $9M, rank #1357. 24,081 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $655K (GeckoTerminal, all pools). 24h trading volume $1.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $453K (GeckoTerminal, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance; a copy of the coin from its home chain (solana), minted here by LayerZero (lzReceive). Tokenomics — Supply: minted here by LayerZero (lzReceive) against tokens locked or burned on other chains. Control: a 3-of-4 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $655K of DEX liquidity across 20 pools. Launch: 282 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb2d9...f3ab`](https://bscscan.com/address/0xb2d97c4ed2d0ef452654f5cab3da3735b5e6f3ab) |
| **Network** | BNB Chain |
| **Price** | $0.0043132 |
| **24h Volume** | $453.4K |
| **Liquidity** | $591.1K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 89.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2976 buys / 3409 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xb2d97c4ed2d0ef452654f5cab3da3735b5e6f3ab)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fight-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
