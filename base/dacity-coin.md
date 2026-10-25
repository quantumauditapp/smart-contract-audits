---
token: Dacity Coin
ticker: DACITY
network: base
risk_score: 55
status: medium
date: 2026-10-25
---

# Dacity Coin (DACITY) — Smart Contract Security Analysis | Base

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dacity-coin-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation rates and pool access. While the code follows standard OpenZeppelin patterns, the high degree of administrative control presents significant trust requirements for token holders.

> **Final Recommendation:** To improve security, consider transitioning the ownership to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with a single privileged address. Additionally, implementing a timelock on sensitive functions like updateMintRate would provide community members with advance notice of supply changes.

Ensure that all administrative actions are documented and communicated transparently to the community. Regularly monitor the contract state to ensure that the owner's actions remain within the expected parameters defined in the protocol's whitepaper.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to standard implementations. 7.3… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are highly centralized. The owner has the authority to mint tokens and halt pool transfers, which directly impacts 7.4 Economic stability. These powers are not… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable, ensuring that the current administrative functions cannot be changed without a new deployment. This provides… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to call updateMintRate and release, which can increase the total supply of the token. This allows the owner to dilute the holdings of all existing token holders at their discretion.

**Recommendation:** Implement a timelock for minting operations or transition ownership to a decentralized governance model to prevent arbitrary supply increases.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to enable or disable token transfers. This gives the owner the power to effectively freeze liquidity or prevent users from moving their assets.

**Recommendation:** Remove the ability to halt transfers or restrict this functionality to emergency scenarios governed by a multi-sig or time-locked contract.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,066 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,066 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $460K (DexScreener, all pools). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $460K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf883...5c7d`](https://basescan.org/address/0xf883836ba4ace2c7625484b5e50cb1c7417b5c7d) |
| **Network** | Base |
| **Price** | $0.9433 |
| **24h Volume** | $1.28M |
| **Liquidity** | $459.7K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 9h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 962 buys / 945 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x1625e37c90a13a550086d95f9dd7dbfdc5aaebbbad140331406eb48bc3bd08bd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dacity-coin-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
