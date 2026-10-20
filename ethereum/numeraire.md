---
token: Numeraire
ticker: NMR
network: ethereum
risk_score: 64
status: medium
date: 2026-09-29
---

# Numeraire (NMR) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/numeraire-eth)

---

## Audit Summary

The UpgradeDelegate contract, serving as an implementation for a proxy, manages token-like balances with significant administrative control. Key findings include the ability for privileged roles to mint new tokens, directly manipulate user balances, and issues related to mapping deletion and an uninitialized state variable. These capabilities introduce considerable economic and technical risks due to the high degree of centralization and potential for misuse by authorized addresses.

> **Final Recommendation:** It is critical to review and restrict the powerful administrative functions within the `UpgradeDelegate` contract. Specifically, the `numeraiTransfer` and `withdraw` functions grant excessive control to privileged roles, enabling token minting and arbitrary balance manipulation. Consider implementing multi-signature wallets for these critical operations and explore time-locks to provide transparency and reaction time for token holders.

Furthermore, address the identified code quality issues, particularly the uninitialized state variable, to ensure predictable and secure contract execution. A comprehensive review of the custom proxy implementation is also recommended to mitigate risks associated with upgrades and ensure its robustness.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract includes an `emergencyStop()` function, restricted to the owner, which can halt operations, providing a safety mechanism (7.8 Operations). However, the contract exhibits significant… |
| **Governance / Economics** | 1/10 | High | The `emergencyStop()` function provides a centralized control point to mitigate ongoing economic damage in an emergency (7.4 Economic, 7.5 Governance). However, the economic model is highly… |
| **Upgrades** | 2/10 | High | The contract is part of a proxy architecture, allowing for future upgrades to fix bugs or add features without migrating user funds (7.7 Upgrades). However, the use of a custom proxy pattern, as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 92.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 3 Medium · ⚪ 4 Informational_

### `CD-02` — A critical function relies on an uninitialized value, potentially leading to incorrect calculations.  *(Severity: High · Status: Unresolved)*

The `getMintable` function uses a state variable that has never been assigned a value. This means the function's output will be based on a default or garbage value, which could lead to incorrect calculations or unexpected behavior, potentially affecting the minting logic or other critical operations.

**Recommendation:** Token holders should be concerned that a function related to minting might not operate correctly due to a programming error. It is strongly recommended that the project team initialize all state variables before use, especially those impacting critical logic like `getMintable`, to ensure the contract behaves as expected and prevents potential exploits or economic discrepancies.


### `CP-02` — Tournament administrator can take or move anyone's tokens.  *(Severity: High · Status: Unresolved)*

The `withdraw` function, controlled by the `tournament` administrator, can directly modify any token holder's balance. This means the `tournament` administrator can burn tokens from any address or move them to another address without the holder's permission.

**Recommendation:** Token holders face a significant risk as the `tournament` administrator can arbitrarily seize or move their tokens. It is strongly recommended that this power be removed or severely restricted, ideally requiring explicit user consent for any token movement, or placing it under a robust, transparent governance mechanism.


### `CD-01` — Certain administrative actions can unintentionally clear important data.  *(Severity: Medium · Status: Unresolved)*

The `createRound` and `numeraiTransfer` functions perform operations that can delete entries from mappings. While this might be intended in some cases, it can also lead to unexpected loss of data or state, potentially causing incorrect behavior or loss of funds if not handled carefully.

**Recommendation:** Token holders should be aware that administrative actions might clear certain data points. It is recommended that the project team ensure that mapping deletions are always intentional and thoroughly tested to prevent accidental data loss or state corruption that could impact the system's integrity.


### `CP-01` — Administrator can create new tokens, diluting existing holders.  *(Severity: Medium · Status: Unresolved)*

The `numeraiTransfer` function allows the contract's owner to create new tokens out of thin air. This increases the total supply, which can reduce the value of tokens held by everyone else without their consent.

**Recommendation:** Token holders should be aware that the contract owner has the power to mint an unlimited number of new tokens. It is recommended that the ability to mint new tokens be removed or placed under strict, transparent governance control, such as a multi-signature wallet with a time-lock.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0xf58b…9131 — holds 92.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 72% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 57.9% of supply. What remains: 27.5% in wallets, 30.4% in other contracts. 42,142 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Numeraire (NMR), market cap $83M, rank #336. On GoPlus's list of trusted tokens. Traded on Binance, Coinbase. 42,142 holders. Verified by: CoinGecko, GoPlus, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $255K (DexScreener, all pools). 24h trading volume $65.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $594K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $255K of DEX liquidity across 8 pools. Launch: 1982 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1776...6671`](https://etherscan.io/address/0x1776e1f26f98b1a5df9cd347953a26dd3cb46671) |
| **Network** | Ethereum |
| **Price** | $12.5200 |
| **24h Volume** | $432.9K |
| **Liquidity** | $182.7K |
| **Volume / Liquidity** | 2.4× |
| **Token Age** | 5y |
| **Top-10 Holders** | 57.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 605 buys / 505 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xde9207a409e92b8ce53435694f78390358acfd1d8ed710ef55a53aa0daf6c4b0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/numeraire-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-29*
