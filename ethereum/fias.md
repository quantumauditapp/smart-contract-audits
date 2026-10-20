---
token: Fias
ticker: FIAS
network: ethereum
risk_score: 56
status: medium
date: 2026-09-29
---

# Fias (FIAS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fias-eth)

---

## Audit Summary

The Fias contract is an upgradeable ERC-20 token. It implements standard token functionalities including `transfer`, `transferFrom`, and `approve`. A key feature is the `multiTransfer` function, which allows sending tokens to multiple recipients in a single transaction. The audit identified one high-severity finding related to the unchecked return value of `transferFrom` calls within the `multiTransfer` function, which could lead to misleading success if the underlying `transferFrom` behavior were to change.

> **Final Recommendation:** It is crucial to address the identified high-severity finding by implementing explicit return value checks for `transferFrom` calls within the `multiTransfer` function. This will enhance the robustness of the token distribution mechanism and prevent potential silent failures, ensuring that all multi-transfers behave as expected. Additionally, ensure that the proxy contract (if deployed) is properly secured and that upgrade procedures are thoroughly tested and follow best practices to maintain the integrity of the token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Fias contract is an ERC-20 token designed for upgradeability, inheriting from `ERC20Upgradeable` and `Initializable`. It provides standard token functionalities such as `transfer`… |
| **Governance / Economics** | 1/10 | High | The Fias contract implements a standard ERC-20 token economic model (7.4 Economic), with no complex tokenomics, staking, or lending mechanisms. The `multiTransfer` function facilitates token… |
| **Upgrades** | 6/10 | Medium | The Fias contract is designed as an upgradeable token, inheriting from `ERC20Upgradeable` and `Initializable` (7.7 Upgrades). This design allows for future enhancements or bug fixes without deploying… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 4 Informational_

### `CD-01` — Potential for misleading success in multi-transfers if `transferFrom` behavior changes.  *(Severity: High · Status: Unresolved)*

The `multiTransfer` function, which allows a user to send Fias tokens to multiple recipients in a single transaction, calls `this.transferFrom` for each individual transfer. While the current `ERC20Upgradeable` implementation of `transferFrom` will revert the entire transaction if any individual transfer fails (e.g., due to insufficient balance), it is a best practice to explicitly check the boolean return value of external calls, especially for ERC-20 `transfer` and `transferFrom` functions. If the underlying `transferFrom` implementation were ever changed or overridden to return `false` on failure instead of reverting, the `multiTransfer` function would not detect these individual failure…

**Recommendation:** To enhance robustness and guard against future changes in `transferFrom` behavior, it is recommended to explicitly check the boolean return value of `this.transferFrom(msg.sender, recipients[i], amounts[i])` within the `multiTransfer` function. If a transfer returns `false`, the function should either revert the entire transaction or log the failure for specific recipients, ensuring transparent and reliable multi-transfers.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x657c…6c83 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 69.8% of supply. Of that, 14.3% burned, 5.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 49.1% in wallets, 0.8% in other contracts. 2,306 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as FIAS (FIAS), rank #3351. 2,306 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $38K (DexScreener, all pools). 24h trading volume $36K (CoinGecko, all markets, daily snapshot). 24h trading volume $78K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner key. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $38K of DEX liquidity across 1 pools. Launch: 652 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8e4f...5585`](https://etherscan.io/address/0x8e4f1ce473b292d56934c36976356e3e22c35585) |
| **Network** | Ethereum |
| **Price** | $0.0006103 |
| **24h Volume** | $77.6K |
| **Liquidity** | $37.9K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 69.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 91 buys / 86 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x21e88f4482cd48deab1ca5eddabdfb14cb8ad76f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fias-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-29*
