---
token: MAKEFOURGREATAGAIN
ticker: M4GA
network: bsc
risk_score: 36
status: medium
date: 2026-11-05
---

# MAKEFOURGREATAGAIN (M4GA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/makefourgreatagain-bsc)

---

## Audit Summary

The Token contract is a standard ERC-20 implementation with an additional mode-switching mechanism. Ownership has been renounced, effectively locking the administrative functions and ensuring the contract operates in a decentralized, immutable state. The code follows standard patterns and exhibits no critical vulnerabilities.

> **Final Recommendation:** The contract is secure and requires no further action as ownership has been renounced. Users should be aware that the transfer logic is fixed and cannot be altered by any party.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements the ERC-20 standard correctly using OpenZeppelin-like primitives. 7.1 Architecture is modular, 7.2 Code Security is robust, and 7.3 Access Control is enforced via Ownable. 7.6… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance risks are mitigated by the renunciation of ownership. No centralized entity can manipulate the token supply or transfer rules. The economic model is fixed and… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are stable due to the immutable nature of the code. The contract is permanently locked in its current state. |

## Security Findings

_⚪ 6 Informational_

### `CP-05` — Immutable Transfer Control Switch  *(Severity: Informational · Status: Unresolved)*

The contract contains a 'setMode' function that allows an owner to toggle transfer rules. Because ownership has been renounced, this function is now permanently disabled and cannot be called by anyone.

**Recommendation:** No action required; the renunciation of ownership serves as a permanent security control for this feature.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 0.0% in wallets, 100.0% in other contracts. 1 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $15K (DexScreener, all pools). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on four.meme, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $15K of DEX liquidity across 2 pools. Launch: launched on four.meme, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x085b...4444`](https://bscscan.com/address/0x085b526f5e1715abc6d6b64046d9d6c91de04444) |
| **Network** | BNB Chain |
| **Price** | $0.00001582 |
| **24h Volume** | $1.08M |
| **Liquidity** | $15.1K |
| **Volume / Liquidity** | 72.0× |
| **Token Age** | 7h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7300 buys / 11550 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x9335d3468bb65fdb7e8b851df3549eab106e7f8c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/makefourgreatagain-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
