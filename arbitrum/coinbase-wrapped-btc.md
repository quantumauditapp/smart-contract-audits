---
token: Coinbase Wrapped BTC
ticker: CBBTC
network: arbitrum
risk_score: 74
status: critical
date: 2026-08-11
---

# Coinbase Wrapped BTC (CBBTC) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 74/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-btc-arb)

---

## Audit Summary

The audit of the FiatTokenV2_1 implementation contract identified a critical access control vulnerability in its initialization function, which could lead to unauthorized fund transfers and contract blacklisting. While the contract leverages well-audited OpenZeppelin libraries for core functionalities, the lack of proper protection for upgrade-specific logic poses a significant risk. Further, the absence of the base FiatTokenV2 contract code limits the scope of a comprehensive assessment.

> **Final Recommendation:** Immediately implement robust access control (e.g., `onlyOwner` or `onlyProxyAdmin`) for the `initializeV2_1` function to prevent unauthorized execution of critical state changes. Ensure that the `lostAndFound` address is a secure, multi-signature controlled wallet. Conduct a full audit of the `FiatTokenV2` base contract to identify any underlying vulnerabilities that could impact the overall system.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract utilizes well-audited OpenZeppelin libraries like SafeMath and SafeERC20, enhancing code security against common integer and ERC-20 interaction vulnerabilities (7.2 Code Security).… |
| **Governance / Economics** | 1/10 | High | The primary governance and economic risk stems from the unprotected `initializeV2_1` function, which can be called by anyone if `_initializedVersion` is 1, leading to unauthorized transfer of… |
| **Upgrades** | 1/10 | High | As an implementation contract for a proxy, upgrade safety is paramount (7.1 Architecture). The `initializeV2_1` function is designed for post-upgrade setup but critically lacks access control, making… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Zeppelin Os Legacy |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 71.2% |
| **Top-3 Unlocked** | ⚠️ 91.5% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Lack of Access Control on `initializeV2_1` Function  *(Severity: Critical · Status: Unresolved)*

The `initializeV2_1` function, intended for upgrade-specific initialization, lacks proper access control. It only checks `_initializedVersion == 1` but does not restrict *who* can call it. If the `_initializedVersion` state variable is set to 1 (e.g., by a previous `initialize` call in `FiatTokenV2`), any external caller can execute this function. This allows unauthorized parties to trigger critical state changes.

**Recommendation:** Implement a robust access control mechanism (e.g., `onlyOwner` or `onlyProxyAdmin`) for the `initializeV2_1` function. Ensure that the `_initializedVersion` state is managed carefully across upgrades and that initialization functions are called only by authorized entities, typically the proxy admin.


### `H-01` — Critical State Changes in Unprotected `initializeV2_1`  *(Severity: High · Status: Unresolved)*

The `initializeV2_1` function performs two critical and irreversible state changes: transferring all tokens held by the contract (`balances[address(this)]`) to a `lostAndFound` address and then blacklisting the contract itself. Due to the lack of access control (C-01), an unauthorized caller could trigger these actions. If the `lostAndFound` address is incorrect or compromised, funds could be permanently lost. Blacklisting the contract prevents it from holding or transferring tokens, which could disrupt operational flows if not fully anticipated.

**Recommendation:** Thoroughly review the necessity and implications of these actions. Ensure the `lostAndFound` address is secure and correctly configured, ideally a multi-signature wallet. Document the operational impact of blacklisting the contract address. Consider adding a timelock or multi-party confirmation for such critical operations.


### `M-01` — Incomplete Audit Scope (Missing `FiatTokenV2` Source)  *(Severity: Medium · Status: Unresolved)*

The provided source code is for `FiatTokenV2_1`, which inherits from `FiatTokenV2`. The full source code for `FiatTokenV2` was not provided, limiting the ability to conduct a comprehensive audit of the entire token logic, including its initialization, access control, and core ERC-20 functionalities. Potential vulnerabilities in the base contract could affect the `FiatTokenV2_1` implementation.

**Recommendation:** Provide the complete source code for all inherited contracts (`FiatTokenV2` and any further dependencies) for a full security assessment of the entire system.


### `L-01` — Use of Older Solidity Version and OpenZeppelin Libraries  *(Severity: Low · Status: Unresolved)*

The contract uses Solidity `0.6.12` and corresponding OpenZeppelin libraries. While `0.6.x` is generally stable, newer Solidity versions (e.g., `0.8.x`) offer built-in overflow/underflow checks, reducing reliance on `SafeMath`, and other compiler optimizations. This can lead to minor gas inefficiencies and potential exposure to subtle compiler bugs present in older versions.

**Recommendation:** Consider upgrading to a more recent Solidity compiler version (e.g., `0.8.x`) and the latest compatible OpenZeppelin contracts to benefit from security enhancements, improved gas efficiency, and modern language features.


### `I-01` — Deliberate Blacklisting of Contract Address  *(Severity: Informational · Status: Unresolved)*

The `initializeV2_1` function explicitly blacklists `address(this)`, meaning the proxy contract itself will be unable to send or receive tokens. This is a deliberate design choice often seen in stablecoins to prevent the token contract from being frozen or having its balance manipulated by external actors or its own functions.

**Recommendation:** Ensure this design choice is well-understood and documented within the project's specifications and operational procedures, as it has specific implications for how the token contract can interact with its own token supply.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcbb7...33bf`](https://arbiscan.io/address/0xcbb7c0000ab88b473b1f5afd9ef808440eed33bf) |
| **Network** | Arbitrum |
| **Price** | $64,172.7300 |
| **24h Volume** | $352.6K |
| **Liquidity** | $539.8K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 58.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 109 buys / 106 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0x9b42809aaae8d088ee01fe637e948784730f0386)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-btc-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
