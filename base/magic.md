---
token: MAGIC
ticker: MAGIC
network: base
risk_score: 71
status: high
date: 2026-10-07
---

# MAGIC (MAGIC) — Smart Contract Security Analysis | Base

> **Risk Score: 71/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/magic-base)

---

## Audit Summary

The MagicBridgeBase contract, deployed as a UUPS proxy, functions as a cross-chain bridge and an ERC-20 token. It enables token transfers across different chains and includes standard ERC-20 functionalities. The contract is owned, granting the owner significant control over bridge configurations, administrative functions, and upgrades. Two high-severity technical findings were identified, related to potential fund locking due to `msg.value` handling and state variable shadowing.

> **Final Recommendation:** Address the identified high-severity technical vulnerabilities promptly to prevent potential fund loss and ensure contract stability. Specifically, review the `_dispatch` function's Ether handling and resolve all instances of state variable shadowing. Implement robust multi-signature or time-lock mechanisms for critical administrative functions, especially those related to upgrades and significant parameter changes, to mitigate the risks associated with centralized owner control.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements a cross-chain bridge with ERC-20 token functionalities, including `transferRemote` for sending tokens across chains and standard ERC-20 operations like `transfer` and… |
| **Governance / Economics** | 1/10 | High | The contract utilizes an `OwnableUpgradeable` pattern, granting the owner extensive control over critical bridge parameters and administrative functions. The owner can `setDestinationGas` to… |
| **Upgrades** | 1/10 | High | The contract is deployed as a UUPS proxy, allowing for future upgrades of its logic. The `upgradeToAndCall` function, which facilitates these upgrades, is restricted to a specific role or the proxy… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 4 Informational_

### `CD-01` — Funds Sent to Non-Payable Function  *(Severity: High · Status: Unresolved)*

The `transferRemote` functions are marked as `payable`, allowing users to send Ether along with their token transfers. However, the internal `_dispatch` function (or a function it calls) is identified as non-payable, meaning it is not designed to receive or handle Ether. If Ether is sent to this non-payable function, it could become permanently locked within the contract, making it inaccessible to users or the protocol.

**Recommendation:** Ensure that any function receiving `msg.value` is explicitly marked `payable` and includes logic to properly handle or forward the received Ether. If `_dispatch` is not intended to receive Ether, the `transferRemote` functions should either remove the `payable` keyword or ensure that `msg.value` is handled before calling `_dispatch`.


### `CD-02` — State Variable Shadowing  *(Severity: High · Status: Unresolved)*

The contract contains instances where a state variable is 'shadowed' by another variable (e.g., a local variable or an inherited variable with the same name). This can lead to confusion for developers and potentially cause the contract to use an incorrect variable value, leading to unexpected behavior or logic errors, especially in complex inheritance hierarchies.

**Recommendation:** Rename shadowed variables to ensure unique identifiers across the contract's scope and its inheritance chain. This improves code clarity and prevents accidental use of the wrong variable, enhancing the contract's reliability.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0x7f4e…15ca — holds 99.8% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 92.0% of supply. Of that, 52.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 23.4% in wallets, 15.9% in other contracts. 744 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Treasure (MAGIC), market cap $23M, rank #802. 744 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $318K (DexScreener, all pools). 24h trading volume $29.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $106K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $6.32 on 2022-02-19; the price is now 98.9108% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: upgradeable proxy. Fees: no buy or sell tax. Market: $318K of DEX liquidity across 1 pools. Launch: 343 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf157...3f43`](https://basescan.org/address/0xf1572d1da5c3cce14ee5a1c9327d17e9ff0e3f43) |
| **Network** | Base |
| **Price** | $0.06799 |
| **24h Volume** | $106.1K |
| **Liquidity** | $317.5K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 92.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 754 buys / 825 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x3c0ae164970ab9ec216cf1b7ae3118766ab65e43)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/magic-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-07*
