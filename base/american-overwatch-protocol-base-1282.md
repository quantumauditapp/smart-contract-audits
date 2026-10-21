---
token: American Overwatch Protocol
ticker: AOP
network: base
risk_score: 60
status: medium
date: 2026-10-21
---

# American Overwatch Protocol (AOP) — Smart Contract Security Analysis | Base

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-base-1282)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance and vesting features. The protocol relies heavily on a centralized owner to manage token supply inflation and liquidity pool access. While the code follows standard OpenZeppelin patterns, the high degree of administrative control presents a significant centralization risk to token holders.

> **Final Recommendation:** To improve security, consider transitioning ownership to a decentralized governance model, such as a multi-signature wallet or a DAO, to mitigate the risks associated with a single point of failure. Implementing a timelock on sensitive administrative functions like updateMintRate would provide transparency and allow the community to react to significant changes in token supply.

Ensure that the owner's private keys are managed with institutional-grade security practices. Regularly audit the vesting schedules and minting parameters to ensure they remain aligned with the protocol's long-term economic objectives.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20 and governance functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard, battle-tested… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are centralized under the contract owner. The owner has the ability to mint tokens and toggle pool access, which directly impacts 7.6 External liquidity… |
| **Upgrades** | 3/10 | High | The contract is not upgradeable, which eliminates 7.7 Upgrades risks. 7.8 Operations are straightforward, relying on the owner to trigger vesting and minting events. The lack of proxy patterns… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to call updateMintRate and release, which can increase the total supply of tokens. This allows the owner to dilute the holdings of existing token holders at their discretion.

**Recommendation:** Implement a timelock for all supply-altering functions or transition ownership to a community-governed DAO to prevent unilateral changes to the token supply.


### `CP-05` — Centralized Control Over Transfer Functionality  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to enable or disable transfers for specific liquidity pools. This grants the owner the power to effectively freeze user funds or prevent trading activity.

**Recommendation:** Remove the ability to arbitrarily lock pools or restrict this functionality to a decentralized governance vote to ensure that liquidity remains accessible to users.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.3% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,038 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,038 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $52K (DexScreener, all pools). 24h trading volume $142K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $52K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd522...d49c`](https://basescan.org/address/0xd522ca7f83053c0e21a2199f566db9da6c6ed49c) |
| **Network** | Base |
| **Price** | $0.005187 |
| **24h Volume** | $142.2K |
| **Liquidity** | $51.5K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 10h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1111 buys / 1072 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x57334e81d2bb7f666451f26a128fc5ec7dcb61987bb05620a683cbe8cbcbaf2c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-base-1282)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
