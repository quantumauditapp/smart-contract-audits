---
token: MemeCore
ticker: M
network: bsc
risk_score: 58
status: medium
date: 2026-10-23
---

# MemeCore (M) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/memecore-bsc)

---

## Audit Summary

The MemeCore token is a standard ERC-20 implementation utilizing the UUPS proxy pattern. The contract includes centralized administrative controls for blacklisting addresses and managing minter allowances. No critical vulnerabilities were identified during the static analysis of the provided source code.

> **Final Recommendation:** The protocol is well-implemented. To further enhance security, consider implementing a multi-signature wallet (e.g., Safe) as the owner to mitigate the risk of a single private key compromise. Additionally, consider adding a timelock controller for administrative actions like blacklisting or minting to provide transparency and a window for community response.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The architecture follows standard OpenZeppelin patterns for UUPS proxies and ERC-20 compliance. 7.1 Architecture is robust, utilizing modular storage locations to prevent collisions. 7.2 Code… |
| **Governance / Economics** | 1/10 | High | The protocol relies on a centralized owner for 7.4 Economic and 7.5 Governance operations. The owner has the power to blacklist any address, effectively freezing funds, and can mint new tokens via… |
| **Upgrades** | 1/10 | High | The contract utilizes 7.7 Upgrades via the UUPS pattern, which is the industry standard for gas-efficient and secure proxy management. 7.8 Operations are supported by the Ownable2Step pattern, which… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 47.2% |
| **Top-3 Unlocked** | ⚠️ 94.9% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.7% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 82% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — a contract — mint new supply; freeze or blacklist individual addresses. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 96.6% of supply. What remains: 95.3% in wallets, 1.4% in other contracts. 8,604 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as MemeCore (M), market cap $1.9B, rank #52. 8,604 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $63K (DexScreener, all pools). 24h trading volume $3.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $128K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $63K of DEX liquidity across 2 pools. Launch: 477 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x22b1...31fa`](https://bscscan.com/address/0x22b1458e780f8fa71e2f84502cee8b5a3cc731fa) |
| **Network** | BNB Chain |
| **Price** | $0.8956 |
| **24h Volume** | $103.0K |
| **Liquidity** | $52.2K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 96.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 683 buys / 662 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x688aa9136e2d48c4cd4f117a40029c6bc18506f6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/memecore-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
