---
token: UDR
ticker: UDR
network: base
risk_score: 57
status: medium
date: 2026-10-22
---

# UDR (UDR) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/udr-base-96b6)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance, voting, and vesting capabilities. The protocol relies on a centralized owner to manage minting rates and pool transfer restrictions. While the code follows standard OpenZeppelin patterns, the high level of administrative control over token supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** Token holders should be aware that the contract owner possesses significant authority to influence token supply and liquidity. It is recommended that the project team considers transitioning ownership to a decentralized multi-signature wallet or a DAO-governed contract to mitigate single-point-of-failure risks.

Furthermore, the team should provide clear documentation regarding the 'pool' lock mechanism to ensure transparency for users interacting with liquidity pools. Regular audits of the owner's wallet security are advised given the extent of the privileged functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, voting, and permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the owner. The owner has the ability to mint tokens up to a 2% annual cap and toggle transferability via the pool lock mechanism.… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not implemented as this is a standard non-proxy contract. 7.8 Operations are straightforward, relying on standard ownership management. No complex upgrade paths exist that could… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to increase the total supply of tokens. This allows the owner to dilute existing holders up to a 2% annual inflation rate.

**Recommendation:** Consider implementing a time-lock on minting functions or moving the minting authority to a decentralized governance contract to increase transparency and trust.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to enable or disable transfers for specific pools. This gives the owner the power to effectively freeze liquidity or restrict trading at their discretion.

**Recommendation:** Document the specific conditions under which these functions will be used and consider adding a timelock to these administrative actions to prevent sudden, unexpected restrictions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 3,010 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,010 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $51K (DexScreener, all pools). 24h trading volume $51K (DexScreener, all pools).

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
| **Contract** | [`0x41d7...e8de`](https://basescan.org/address/0x41d728ca0fa00abae803761247c621eaac84e8de) |
| **Network** | Base |
| **Price** | $0.005042 |
| **24h Volume** | $50.7K |
| **Liquidity** | $50.8K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 12h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2274 buys / 1512 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xc7049cd57cc7fee6c5c6ae4dd8da8e56c5a9d378d871af89646710175e3e6ccb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/udr-base-96b6)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
