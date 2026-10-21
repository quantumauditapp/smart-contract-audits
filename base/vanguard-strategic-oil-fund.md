---
token: Vanguard Strategic Oil Fund
ticker: VSOF
network: base
risk_score: 60
status: medium
date: 2026-10-21
---

# Vanguard Strategic Oil Fund (VSOF) — Smart Contract Security Analysis | Base

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vanguard-strategic-oil-fund-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation rates and liquidity pool access. While the code follows standard OpenZeppelin patterns, the high level of administrative control over token supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** Token holders should be aware that the contract owner possesses significant control over the token's economic parameters and transferability. It is recommended that the project transition to a decentralized governance model, such as a multi-signature wallet or a DAO, to mitigate the risks associated with a single point of failure.

Furthermore, ensure that all administrative actions are transparently communicated to the community. Consider implementing a timelock on sensitive functions like updateMintRate to provide users with advance notice of changes to the token supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner has the ability to mint tokens up to a 2% annual cap and toggle transferability via the pool lock mechanism. This creates a… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not implemented; the contract is immutable. 7.8 Operations are limited to the owner's ability to adjust parameters. No proxy patterns are present, ensuring the logic cannot be… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to increase the total supply of tokens. This allows the owner to dilute the holdings of all existing token holders at their discretion, provided they stay within the 2% annual inflation limit.

**Recommendation:** Implement a timelock on the updateMintRate function or transition ownership to a decentralized governance contract to prevent unilateral supply changes.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to enable or disable transfers for specific pools. This gives the owner the power to effectively freeze liquidity or restrict user access to trading at any time.

**Recommendation:** Restrict the use of pool locking to emergency scenarios only and document the specific conditions under which this function would be invoked to maintain transparency.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.1% in wallets, 80.1% in other contracts. The deployer/owner wallet itself holds 16.1%. 3,018 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,018 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $51K (DexScreener, all pools). 24h trading volume $34K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $51K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd91a...bc43`](https://basescan.org/address/0xd91a4188a0e2d7b72a5923acf0c18295603bbc43) |
| **Network** | Base |
| **Price** | $0.002503 |
| **24h Volume** | $34.4K |
| **Liquidity** | $51.0K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 23h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2047 buys / 1368 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xaaaced4909a6301a3d64bc88b02ec3c98c1f1637e2f81ca78f58784924789c81)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vanguard-strategic-oil-fund-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
