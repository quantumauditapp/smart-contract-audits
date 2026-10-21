---
token: United States Dividend  Fund
ticker: USDF
network: base
risk_score: 61
status: medium
date: 2026-10-21
---

# United States Dividend  Fund (USDF) — Smart Contract Security Analysis | Base

> **Risk Score: 61/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-base-1560)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation, pool locking, and token metadata. While the code follows standard OpenZeppelin patterns, the high level of administrative control over token supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** To improve security and trust, consider transitioning ownership to a multi-signature wallet or a decentralized governance contract (DAO). This would mitigate the risk of a single point of failure and provide transparency for administrative actions like minting or pool locking.

Additionally, implement a timelock mechanism for all privileged functions. A delay of 24-48 hours for actions like updateMintRate or lockPool would allow the community to react to administrative changes, significantly reducing the risk of sudden, malicious, or accidental state modifications.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-tested OpenZeppelin libraries for ERC-20 and governance functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard, audited base… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner has the authority to mint tokens and restrict transferability, which directly impacts the token's market value and… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not supported as the contract is not a proxy. This provides immutability, which is a strength for trustless operation. However, it also means that any logic errors discovered… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply at their discretion, which can dilute the value of existing holdings.

**Recommendation:** Implement a timelock on minting functions or transition ownership to a decentralized governance model to ensure that supply changes are subject to community consensus.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to enable or disable token transfers. This gives the owner the power to freeze user funds or prevent trading activity at any time.

**Recommendation:** Remove the ability to arbitrarily lock transfers, or if required for specific pool mechanics, ensure the logic is strictly bounded and transparently documented to prevent misuse.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.3% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.3%. 2,042 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,042 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $52K (DexScreener, all pools). 24h trading volume $151K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.005262 — it does not hold a peg. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $52K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1c36...fd7f`](https://basescan.org/address/0x1c36a1b073f7001e705a72aeaa4c9d32b2cafd7f) |
| **Network** | Base |
| **Price** | $0.005262 |
| **24h Volume** | $150.8K |
| **Liquidity** | $51.7K |
| **Volume / Liquidity** | 2.9× |
| **Token Age** | 10h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1126 buys / 1087 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xf54c750f7de6ff9bcd506e6d2c6dc5bafb046b1ae70a3239d44ea66a42f63988)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-base-1560)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
