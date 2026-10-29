---
token: PARTI Token
ticker: PARTI
network: bsc
risk_score: 56
status: medium
date: 2026-10-29
---

# PARTI Token (PARTI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/parti-token-bsc)

---

## Audit Summary

ParticleToken is an Omnichain Fungible Token (OFT) implementation utilizing LayerZero infrastructure. The architecture follows standard OFT patterns for cross-chain interoperability. While the contract allows for minting via cross-chain messaging, this is inherent to the OFT design. 7.1 Architecture: Standard OFT. 7.2 Code Security: High. 7.3 Access Control: Robust. 7.4 Economic: Standard. 7.5 Governance: Multisig. 7.6 External: LayerZero. 7.7 Upgrades: N/A. 7.8 Operations: Standard.

> **Final Recommendation:** The protocol demonstrates a solid security posture with standard implementations. We recommend maintaining the multisig threshold and ensuring that the LayerZero endpoint configuration remains monitored for any updates or security advisories from the LayerZero team.

Users should monitor the total supply and cross-chain bridge activity, as the minting mechanism is inherently linked to the OFT cross-chain messaging protocol.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited LayerZero OFT libraries for cross-chain token transfers. The codebase is clean and adheres to standard ERC-20 and EIP-712 specifications. The primary technical risk… |
| **Governance / Economics** | 1/10 | High | Governance is managed via a 3-of-4 multisig, providing a reasonable balance between security and operational agility. The economic model relies on the OFT minting mechanism, which is controlled by… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable. Logic is immutable upon deployment. This eliminates risks associated with proxy storage collisions or malicious implementation swaps. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.8% |
| **Top-3 Unlocked** | ⚠️ 99.9% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Dynamic Token Supply via Cross-Chain Minting  *(Severity: Medium · Status: Unresolved)*

The functions send, lzReceiveSimulate, and lzReceive allow the contract to mint new tokens as part of the cross-chain transfer process. This increases the total supply and can dilute existing token holders if the cross-chain bridge is compromised or misconfigured.

**Recommendation:** Ensure that the LayerZero endpoint and the associated peer contracts are strictly managed and monitored. Regularly audit the cross-chain messaging configuration to prevent unauthorized minting events.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x4588…dba1 — holds 99.8% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 84.9% of supply. What remains: 66.3% in wallets, 18.6% in other contracts. 162,212 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Particle Network (PARTI), market cap $9M, rank #1339. Traded on Binance. 162,212 holders. Verified by: exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $578K (DexScreener, all pools). 24h trading volume $8.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $812K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.419 on 2025-05-13; the price is now 90.7115% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-4 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $578K of DEX liquidity across 5 pools. Launch: 584 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5926...0f00`](https://bscscan.com/address/0x59264f02d301281f3393e1385c0aefd446eb0f00) |
| **Network** | BNB Chain |
| **Price** | $0.05694 |
| **24h Volume** | $811.5K |
| **Liquidity** | $578.1K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 84.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2145 buys / 1610 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xc0fb39f705ee65ef098dd5452997a7846d156aa9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/parti-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
