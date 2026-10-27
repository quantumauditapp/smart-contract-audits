---
token: Anthropic
ticker: ANTHROPIC
network: base
risk_score: 74
status: high
date: 2026-10-27
---

# Anthropic (ANTHROPIC) — Smart Contract Security Analysis | Base

> **Risk Score: 74/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anthropic-base)

---

## Audit Summary

The USUPERC20 contract is a standard ERC-20 token implementation extended with cross-chain functionality. The architecture relies on a privileged bridge contract to manage supply via minting and burning. While the core ERC-20 logic is standard, the centralization of power in the bridge contract introduces significant trust requirements for token holders.

> **Final Recommendation:** Token holders should be aware that the bridge contract holds significant power over the token supply and individual balances. We recommend that the bridge contract be governed by a multi-signature wallet or a decentralized DAO to mitigate the risk of a single point of failure.

Ensure that the bridge contract's own security is audited to the highest standard, as any compromise of the bridge will directly impact the integrity of the USUPERC20 token. Monitor the bridge's administrative actions for transparency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract follows standard ERC-20 patterns and implements 7.1 Architecture and 7.2 Code Security effectively. 7.3 Access Control is strictly enforced via the onlySuperchainTokenBridge modifier.… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are centralized within the bridge controller. The ability to mint and burn tokens directly impacts the total supply and individual holdings. Users must trust… |
| **Upgrades** | 3/10 | High | The contract is not currently using a proxy pattern, meaning 7.7 Upgrades are not applicable. 7.8 Operations are stable as the contract logic is immutable. Future changes would require a full… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 5 Informational_

### `CP-02` — Privileged Balance Manipulation  *(Severity: High · Status: Unresolved)*

The crosschainBurn function allows the bridge contract to remove tokens from any user's balance, effectively acting as a force-transfer or burn mechanism.

**Recommendation:** Restrict the burn functionality to only allow users to burn their own tokens, or implement a timelock for administrative burn actions.


### `CP-01` — Privileged Minting Capability  *(Severity: Medium · Status: Unresolved)*

The crosschainMint function allows the designated bridge contract to increase the total supply of tokens at any time, which can dilute the value of existing holdings.

**Recommendation:** Implement a hard cap on the total supply or require a multi-step governance process for large minting events.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xaf8e…2844 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 100.0% in wallets, 0.0% in other contracts. 4,589 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,589 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $502.2M (DexScreener, all pools). 24h trading volume $38.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $502.2M of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6287...a604`](https://basescan.org/address/0x62876fbf56db53662504af0b213a0842d37fa604) |
| **Network** | Base |
| **Price** | $502.5000 |
| **24h Volume** | $38.51M |
| **Liquidity** | $502.16M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 7h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1055 buys / 915 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xbd2eb5b7a3e52dd055def1ed9ebdb116cb0f886d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anthropic-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
