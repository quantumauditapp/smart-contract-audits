---
token: GDollar
ticker: GDLR
network: ethereum
risk_score: 63
status: medium
date: 2026-10-31
---

# GDollar (GDLR) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 63/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gdollar-eth)

---

## Audit Summary

The TokenContract implements a highly centralized ERC-20 token with extensive administrative controls. While the architecture follows standard OpenZeppelin patterns for access control and reentrancy protection, the contract grants extreme power to privileged roles, including the ability to modify user balances, block addresses, and alter transfer economics. The protocol relies on a time-delayed role granting mechanism to mitigate immediate administrative abuse, but the underlying centralization remains a significant risk factor for token holders.

> **Final Recommendation:** The protocol should transition to a decentralized governance model (e.g., a DAO or multi-signature wallet) to manage privileged functions, reducing the risk of single-point-of-failure or malicious admin actions. Additionally, implementing a 'timelock' on all sensitive administrative functions, not just role grants, would significantly increase transparency and security for token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes robust libraries like ReentrancyGuard and AccessControlEnumerable to ensure standard security practices. 7.1 Architecture is modular, separating vault logic from token… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance controls are heavily centralized. The admin can unilaterally change transfer taxes and discount tiers, directly impacting the token's economic model. 7.6 External… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not implemented via proxy patterns in this version. 7.8 Operations are managed through a time-delayed role grant system, which provides a window for community oversight before new… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 4 Medium · ⚪ 4 Informational_

### `CP-02` — Administrative Balance Manipulation  *(Severity: High · Status: Unresolved)*

The burnAndRedeem function allows a privileged address to burn or move tokens from any user's balance. This represents a significant risk to user asset custody.

**Recommendation:** Restrict the ability to burn tokens to the owner of the tokens only, or implement a transparent, time-locked process for any forced balance changes.


### `CP-01` — Privileged Minting Capability  *(Severity: Medium · Status: Unresolved)*

The mint function allows a privileged address to create new tokens, which dilutes the value of existing holdings. This function is restricted to specific roles but lacks a hard cap on total supply.

**Recommendation:** Implement a maximum supply cap or require a multi-signature approval process for all minting operations.


### `CP-06` — Address Blocklisting Capability  *(Severity: Medium · Status: Unresolved)*

Privileged roles can add any address to a blocklist, preventing them from transferring or selling their tokens. This can be used to censor users or freeze assets.

**Recommendation:** Limit the blocklist functionality to specific regulatory compliance scenarios and provide a clear, public justification for any address added to the list.


### `CP-07` — Transfer Fee Manipulation  *(Severity: Medium · Status: Unresolved)*

The admin can change transfer taxes and discount tiers at will. This allows for arbitrary changes to the cost of transacting with the token.

**Recommendation:** Set a hard-coded maximum for transfer taxes and require a governance vote for any changes to the fee structure.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x55b9…0397 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 75.1% of supply. Of that, 43.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 20.3% in wallets, 11.4% in other contracts. 164 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

164 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $193K (DexScreener, all pools). 24h trading volume $99K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $193K of DEX liquidity across 1 pools. Launch: 73 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa038...8e4e`](https://etherscan.io/address/0xa038a26bf960451b8ce75ec4c92013c6307f8e4e) |
| **Network** | Ethereum |
| **Price** | $1.3200 |
| **24h Volume** | $99.3K |
| **Liquidity** | $193.2K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 75.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 92 buys / 32 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xdbf919d8a1276be708736527045b1610df27319f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gdollar-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
