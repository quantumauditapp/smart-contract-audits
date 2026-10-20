---
token: American Trust Fund System
ticker: ATFS
network: base
risk_score: 66
status: high
date: 2026-10-20
---

# American Trust Fund System (ATFS) — Smart Contract Security Analysis | Base

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-trust-fund-system-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting features. The architecture relies heavily on a centralized owner role, which possesses significant control over token supply and transferability. While the code follows standard OpenZeppelin patterns, the centralization of power presents a notable risk to token holders.

> **Final Recommendation:** It is recommended to transition the ownership of the contract to a decentralized governance structure, such as a DAO or a multi-signature wallet, to mitigate the risks associated with centralized control. Implementing a timelock on sensitive functions like updateMintRate and lockPool would provide users with sufficient notice before significant changes to the token's economic parameters occur.

Additionally, consider documenting the specific conditions under which the pool lock mechanism is intended to be used to ensure transparency for the community. Regular audits of the governance process are advised to ensure that the centralization of power does not lead to unintended consequences for token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes well-audited OpenZeppelin libraries for core ERC-20 and governance functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the owner. The owner can manipulate supply via inflation and halt transfers, which directly impacts token liquidity and value.… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable, providing certainty to users regarding the contract's behavior. No upgrade-related risks are present. |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply, which dilutes the value of existing holdings.

**Recommendation:** Implement a timelock for minting operations or transition ownership to a decentralized governance body to prevent arbitrary supply increases.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch using the lockPool and unlockPool functions. This allows the owner to unilaterally halt or resume token transfers, effectively freezing user assets.

**Recommendation:** Restrict the use of transfer-halting functions to emergency scenarios only and implement a transparent, community-governed process for triggering such actions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 14.5% in wallets, 81.8% in other contracts. The deployer/owner wallet itself holds 16.2%. 1,611 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,611 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $30K (DexScreener, all pools). 24h trading volume $175K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $30K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfc16...ff0f`](https://basescan.org/address/0xfc16d545e187116e12830208ff2499b91e73ff0f) |
| **Network** | Base |
| **Price** | $0.00000057 |
| **24h Volume** | $174.8K |
| **Liquidity** | $30.0K |
| **Volume / Liquidity** | 5.8× |
| **Token Age** | 13h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1195 buys / 1188 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xb45207e36e8b646bb0b81d9e00e116a2117e64bb8ce23b448b5a10a2e844ec1a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-trust-fund-system-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
