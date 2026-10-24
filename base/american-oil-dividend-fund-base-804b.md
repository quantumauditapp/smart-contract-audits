---
token: American Oil Dividend Fund
ticker: AODF
network: base
risk_score: 62
status: medium
date: 2026-10-24
---

# American Oil Dividend Fund (AODF) — Smart Contract Security Analysis | Base

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-base-804b)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The architecture relies on a centralized owner account that holds significant power over token supply and transferability. While the code follows standard OpenZeppelin patterns, the centralization of administrative functions poses a risk to token holders.

> **Final Recommendation:** It is recommended to transition the ownership of the contract to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with a single privileged owner. Implementing a timelock on sensitive functions like updateMintRate and lockPool would provide transparency and allow users to react to administrative changes.

Ensure that all administrative actions are documented and communicated to the community to maintain trust. Given the centralization of power, users should be aware that the owner has the technical capability to influence token liquidity and supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-tested OpenZeppelin libraries for ERC-20 and governance features. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard, audited base… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the owner. The owner has the ability to mint tokens and halt transfers, which directly impacts 7.8 Operations. While inflation is… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. This eliminates risks associated with implementation swaps but prevents future logic updates. The current state is immutable regarding… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to increase the total supply of the token. This allows the owner to dilute the holdings of all existing token holders at their discretion, provided they stay within the 2% annual cap.

**Recommendation:** Consider moving the minting authority to a decentralized governance mechanism or a timelocked contract to prevent unilateral supply changes.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to enable or disable transfers for the token. This gives the owner the power to effectively freeze user assets or halt trading activity at any time.

**Recommendation:** Remove the ability to lock transfers or implement a community-driven voting process to trigger such emergency measures.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.1% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,545 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,545 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $47K (DexScreener, all pools). 24h trading volume $101K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $47K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb9db...af4b`](https://basescan.org/address/0xb9db125755db57d58a33f54b81b8409887afaf4b) |
| **Network** | Base |
| **Price** | $0.004604 |
| **24h Volume** | $101.4K |
| **Liquidity** | $46.9K |
| **Volume / Liquidity** | 2.2× |
| **Token Age** | 11h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1394 buys / 1380 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x90e2598ffcd8903144fd4bbc1bfd4948272c9e27de80f6b4cf47c869ebafd647)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-base-804b)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
