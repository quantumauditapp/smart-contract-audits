---
token: Bootr
ticker: BOOTR
network: base
risk_score: 54
status: medium
date: 2026-11-04
---

# Bootr (BOOTR) — Smart Contract Security Analysis | Base

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bootr-base)

---

## Audit Summary

The ClankerToken is an ERC-20 compliant token designed for cross-chain interoperability on the Base network. It utilizes the Superchain Token Bridge for minting and burning operations. While the architecture follows standard cross-chain patterns, the centralization of mint/burn authority poses inherent risks to token holders.

> **Final Recommendation:** Token holders should be aware that the Superchain Token Bridge holds the authority to mint and burn tokens, which is necessary for cross-chain functionality but represents a central point of failure. Ensure that the bridge contract is audited and monitored for any anomalous activity.

Maintain strict security over the admin address, as it controls metadata and administrative settings. Consider implementing a multi-signature wallet for the admin role to mitigate the risk of a single key compromise.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard ERC-20, ERC-20Votes, and ERC-7802 interfaces correctly. 7.1 Architecture is modular, relying on the Superchain Token Bridge for cross-chain state transitions. 7.2… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic risks are present due to the ability of the bridge to alter total supply and individual balances. 7.5 Governance is centralized under an admin role for metadata updates, which is… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not implemented as the contract is not a proxy. 7.8 Operations are limited to metadata and admin management. The lack of upgradeability ensures immutability of the core logic, which… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 7 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Privileged Minting Authority  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the Superchain Token Bridge to increase the total supply of the token. This can lead to the dilution of existing token holders' value if the bridge is compromised or misconfigured. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure the bridge contract is secured with multi-signature requirements and monitor minting events for unexpected spikes in supply.


### `CP-02` — Privileged Balance Manipulation  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the Superchain Token Bridge to remove tokens from any user's balance. This grants the bridge the power to effectively seize or destroy user funds. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement strict circuit breakers or rate limits on the bridge's ability to burn tokens to prevent mass unauthorized balance reduction.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 65.2% of supply. What remains: 6.5% in wallets, 58.8% in other contracts. 260 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

260 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $88K (DexScreener, all pools). 24h trading volume $515K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $88K of DEX liquidity across 4 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb1c3...565c`](https://basescan.org/address/0xb1c3a6ac90e324c4072ad4b2a71c5d9382f9565c) |
| **Network** | Base |
| **Price** | $0.0000013 |
| **24h Volume** | $513.5K |
| **Liquidity** | $87.8K |
| **Volume / Liquidity** | 5.9× |
| **Token Age** | 2h |
| **Top-10 Holders** | 65.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6523 buys / 5770 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x8bc634771ded3d01de173219fe3862bd17f80e887b73f81de09c34bad12aa395)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bootr-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
