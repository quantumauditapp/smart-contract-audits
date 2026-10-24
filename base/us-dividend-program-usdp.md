---
token: US Dividend Program (USDP)
ticker: USDP
network: base
risk_score: 72
status: high
date: 2026-10-24
---

# US Dividend Program (USDP) (USDP) — Smart Contract Security Analysis | Base

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/us-dividend-program-usdp-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with added governance, voting, and vesting capabilities. The protocol relies on a centralized owner to manage inflation, pool locking, and vesting releases. While the code follows standard OpenZeppelin patterns, the high degree of administrative control presents a significant centralization risk to token holders.

> **Final Recommendation:** To improve security and decentralization, consider transitioning ownership to a multi-signature wallet or a DAO governance contract. This would prevent a single point of failure from unilaterally changing the token supply or locking liquidity pools.

Additionally, implement a timelock mechanism for all privileged functions. This would provide transparency to the community and allow users time to react before significant changes to the protocol's economic parameters take effect.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, voting, and access control. 7.1 Architecture is modular, and 7.2 Code Security is robust with no reentrancy or overflow… |
| **Governance / Economics** | 3/10 | High | The economic model is heavily centralized, with 7.4 Economic and 7.5 Governance parameters controlled entirely by the owner. 7.6 External dependencies are minimal, relying on standard block… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, mitigating 7.7 Upgrades risks. 7.8 Operations are handled through direct function calls by the owner. No proxy patterns are utilized, ensuring the logic remains… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply at their discretion, which can lead to the dilution of existing token holders' value.

**Recommendation:** Implement a hard-coded minting schedule or move the minting authority to a decentralized governance contract to prevent arbitrary supply increases.


### `CP-05` — Centralized Control Over Transfer Functionality  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to toggle the ability for users to transfer tokens. This gives the owner the power to freeze user assets or halt trading activity at any time.

**Recommendation:** Remove the ability for the owner to arbitrarily lock transfers, or implement a community-driven voting process to authorize such actions in emergency scenarios.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 10,019 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

10,019 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $161K (DexScreener, all pools). 24h trading volume $735K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.8109 — it does not hold a peg. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $161K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9855...178b`](https://basescan.org/address/0x9855d41114582e5d053109e42d6f38ebba38178b) |
| **Network** | Base |
| **Price** | $0.8109 |
| **24h Volume** | $734.8K |
| **Liquidity** | $161.3K |
| **Volume / Liquidity** | 4.6× |
| **Token Age** | 3h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2010 buys / 1749 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x1740bd503d3f530ac7395c38a11ec73f6c0313aad0aaa2bb08a8063ec641f2e6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/us-dividend-program-usdp-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
