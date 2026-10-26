---
token: Coinbase Wrapped BTC
ticker: CBBTC
network: arbitrum
risk_score: 9
status: low
date: 2026-08-11
---

# Coinbase Wrapped BTC (CBBTC) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-btc-arb)

---

## Audit Summary

The audit of the FiatTokenV2_1 implementation contract identified a critical access control vulnerability in its initialization function, which could lead to unauthorized fund transfers and contract blacklisting. While the contract leverages well-audited OpenZeppelin libraries for core functionalities, the lack of proper protection for upgrade-specific logic poses a significant risk. Further, the absence of the base FiatTokenV2 contract code limits the scope of a comprehensive assessment.

> **Final Recommendation:** Immediately implement robust access control (e.g., `onlyOwner` or `onlyProxyAdmin`) for the `initializeV2_1` function to prevent unauthorized execution of critical state changes. Ensure that the `lostAndFound` address is a secure, multi-signature controlled wallet. Conduct a full audit of the `FiatTokenV2` base contract to identify any underlying vulnerabilities that could impact the overall system.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract utilizes well-audited OpenZeppelin libraries like SafeMath and SafeERC20, enhancing code security against common integer and ERC-20 interaction vulnerabilities (7.2 Code Security).… |
| **Governance / Economics** | 9/10 | Low | The primary governance and economic risk stems from the unprotected `initializeV2_1` function, which can be called by anyone if `_initializedVersion` is 1, leading to unauthorized transfer of… |
| **Upgrades** | 2/10 | High | As an implementation contract for a proxy, upgrade safety is paramount (7.1 Architecture). The `initializeV2_1` function is designed for post-upgrade setup but critically lacks access control, making… |

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
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `M-01` — Incomplete Audit Scope (Missing `FiatTokenV2` Source)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code is for `FiatTokenV2_1`, which inherits from `FiatTokenV2`. The full source code for `FiatTokenV2` was not provided, limiting the ability to conduct a comprehensive audit of the entire token logic, including its initialization, access control, and core ERC-20 functionalities. Potential vulnerabilities in the base contract could affect the `FiatTokenV2_1` implementation.

**Recommendation:** Provide the complete source code for all inherited contracts (`FiatTokenV2` and any further dependencies) for a full security assessment of the entire system.


### `M-02` — Lack of Access Control on `initializeV2_1` Function  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initializeV2_1` function, intended for upgrade-specific initialization, lacks proper access control. It only checks `_initializedVersion == 1` but does not restrict *who* can call it. If the `_initializedVersion` state variable is set to 1 (e.g., by a previous `initialize` call in `FiatTokenV2`), any external caller can execute this function. This allows unauthorized parties to trigger critical state changes.

**Recommendation:** Implement a robust access control mechanism (e.g., `onlyOwner` or `onlyProxyAdmin`) for the `initializeV2_1` function. Ensure that the `_initializedVersion` state is managed carefully across upgrades and that initialization functions are called only by authorized entities, typically the proxy admin.


### `M-03` — Critical State Changes in Unprotected `initializeV2_1`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initializeV2_1` function performs two critical and irreversible state changes: transferring all tokens held by the contract (`balances[address(this)]`) to a `lostAndFound` address and then blacklisting the contract itself. Due to the lack of access control (C-01), an unauthorized caller could trigger these actions. If the `lostAndFound` address is incorrect or compromised, funds could be permanently lost. Blacklisting the contract prevents it from holding or transferring tokens, which could disrupt operational flows if not fully anticipated.

**Recommendation:** Thoroughly review the necessity and implications of these actions. Ensure the `lostAndFound` address is secure and correctly configured, ideally a multi-signature wallet. Document the operational impact of blacklisting the contract address. Consider adding a timelock or multi-party confirmation for such critical operations.


### `L-01` — Use of Older Solidity Version and OpenZeppelin Libraries  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses Solidity `0.6.12` and corresponding OpenZeppelin libraries. While `0.6.x` is generally stable, newer Solidity versions (e.g., `0.8.x`) offer built-in overflow/underflow checks, reducing reliance on `SafeMath`, and other compiler optimizations. This can lead to minor gas inefficiencies and potential exposure to subtle compiler bugs present in older versions.

**Recommendation:** Consider upgrading to a more recent Solidity compiler version (e.g., `0.8.x`) and the latest compatible OpenZeppelin contracts to benefit from security enhancements, improved gas efficiency, and modern language features.


### `I-01` — Deliberate Blacklisting of Contract Address  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initializeV2_1` function explicitly blacklists `address(this)`, meaning the proxy contract itself will be unable to send or receive tokens. This is a deliberate design choice often seen in stablecoins to prevent the token contract from being frozen or having its balance manipulated by external actors or its own functions.

**Recommendation:** Ensure this design choice is well-understood and documented within the project's specifications and operational procedures, as it has specific implications for how the token contract can interact with its own token supply.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 50.8% of supply. What remains: 30.1% in wallets, 20.7% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Coinbase Wrapped BTC (CBBTC), market cap $7.7B. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $894K (DexScreener, all pools). 24h trading volume $1.4M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — a single wallet (EOA) — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Wrapped-Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: a single wallet (EOA). Code: upgradeable proxy. Fees: no buy or sell tax. Market: $894K of DEX liquidity across 2 pools. Launch: 627 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcbb7...33bf`](https://arbiscan.io/address/0xcbb7c0000ab88b473b1f5afd9ef808440eed33bf) |
| **Network** | Arbitrum |
| **Price** | $80,971.3800 |
| **24h Volume** | $1.36M |
| **Liquidity** | $776.1K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 50.8% of supply |
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
