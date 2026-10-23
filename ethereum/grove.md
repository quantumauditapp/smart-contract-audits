---
token: Grove
ticker: GROVE
network: ethereum
risk_score: 51
status: medium
date: 2026-10-23
---

# Grove (GROVE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grove-eth)

---

## Audit Summary

The SDAO contract is a standard ERC-20 token implementation. The codebase is simple, lacks complex administrative privileges, and follows standard patterns for balance management and allowance handling. No vulnerabilities were identified in the transfer logic or state management.

> **Final Recommendation:** The contract is secure and follows standard practices. No changes are required for the current implementation. Ensure that any future integrations with decentralized exchanges or lending protocols verify the token's compliance with the full ERC-20 interface, as some standard functions like totalSupply() are missing from the provided source.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows a standard ERC-20 pattern with no external dependencies. 7.1 Architecture and 7.2 Code Security are robust, utilizing unchecked blocks for gas efficiency where overflow is… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance items are not applicable as the contract is a simple token without staking, minting, or voting mechanisms. The token supply is static, and there are no inflationary or… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. This provides immutability, ensuring that the logic cannot be altered post-deployment. 7.8 Operations are straightforward, requiring no… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 0.0% in wallets, 100.0% in other contracts. 3 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Grove (GROVE), market cap $5M, rank #1659. Traded on Coinbase. 3 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $81K (DexScreener, all pools). 24h trading volume $730K (CoinGecko, all markets, daily snapshot). 24h trading volume $72K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $81K of DEX liquidity across 1 pools. Launch: 58 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb30f...9406`](https://etherscan.io/address/0xb30fe1cf884b48a22a50d22a9282004f2c5e9406) |
| **Network** | Ethereum |
| **Price** | $0.005146 |
| **24h Volume** | $72.1K |
| **Liquidity** | $80.6K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 244 buys / 290 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x0196d365448c076bec48dbf99a5575c1f081ae89a23de1fdaee1d5934c0b9699)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grove-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
