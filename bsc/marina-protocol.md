---
token: Marina Protocol
ticker: BAY
network: bsc
risk_score: 32
status: low
date: 2026-10-08
---

# Marina Protocol (BAY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 32/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/marina-protocol-bsc)

---

## Audit Summary

The BAYToken contract implements a standard ERC-20 token with no custom privileged functions or complex logic. The analysis found no critical, high, or medium severity vulnerabilities. The contract is non-upgradeable, which simplifies its security profile. Overall, the technical and economic risks are assessed as low.

> **Final Recommendation:** Token holders should always verify the contract address when interacting with the token to prevent phishing attacks. Users should understand the token's intended utility and associated ecosystem risks, as this audit focuses solely on the smart contract's code security. Ensure that any platforms or dApps interacting with BAYToken have also undergone thorough security reviews.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The BAYToken contract implements a standard ERC-20 token, providing basic functionalities like `transfer`, `transferFrom`, `approve`, `balanceOf`, and `totalSupply`. The absence of custom privileged… |
| **Governance / Economics** | 5/10 | Medium | As a standard ERC-20 token, BAYToken does not incorporate complex governance mechanisms or unique economic models (7.5 Governance, 7.4 Economic). There are no special minting, burning, or… |
| **Upgrades** | 9/10 | Low | The BAYToken contract is deployed as a standalone, non-upgradeable implementation (7.7 Upgrades). This design choice eliminates risks associated with proxy patterns, such as upgradeability bugs… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x6a10…d2b1 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 97.0% of supply. What remains: 2.1% in wallets, 94.9% in other contracts. 53,644 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Marina Protocol (BAY), market cap $7M, rank #1438. 53,644 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $24K (DexScreener, all pools). 24h trading volume $865K (CoinGecko, all markets, daily snapshot). 24h trading volume $62K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $24K of DEX liquidity across 3 pools. Launch: 341 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa7be...ca25`](https://bscscan.com/address/0xa7bef5abd9265ab97ee43d2fc4a56e0ba25aca25) |
| **Network** | BNB Chain |
| **Price** | $0.03745 |
| **24h Volume** | $62.0K |
| **Liquidity** | $23.9K |
| **Volume / Liquidity** | 2.6× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 97.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 855 buys / 881 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xd1e48e9bb2631ed512ab65c9e6699920c484c3a4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/marina-protocol-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
