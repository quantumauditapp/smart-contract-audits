---
token: Superfluid Token
ticker: SUP
network: base
risk_score: 81
status: high
date: 2026-09-29
---

# Superfluid Token (SUP) — Smart Contract Security Analysis | Base

> **Risk Score: 81/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/superfluid-token-base)

---

## Audit Summary

The SuperToken contract implements an ERC-20 compatible token with Superfluid features, operating as a UUPS proxy. The contract is owned by a multisig and includes extensive privileged functions for managing token supply, balances, and upgradeability. Key findings include a critical vulnerability allowing anyone to initialize or destroy the upgradeable logic, high-severity issues related to privileged balance manipulation and uninitialized state, and medium-severity concerns regarding token minting by privileged addresses.

> **Final Recommendation:** Address the critical vulnerability by ensuring the implementation contract's `initialize` and other sensitive functions are protected from direct external calls, typically by deploying it in an uninitialized state and using an `initializer` modifier. Review and secure all privileged functions, especially those related to token minting and balance manipulation, by implementing strict access controls and multi-signature requirements where appropriate. Finally, ensure all state variables are explicitly initialized to prevent unexpected behavior and review arithmetic operations for potential rounding losses.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The SuperToken contract provides standard ERC-20 functionality alongside advanced Superfluid features, including mechanisms for balance settlement and liquidation payouts (7.1 Architecture). The code… |
| **Governance / Economics** | 1/10 | High | The contract's economic model relies heavily on privileged roles ('host', 'self', 'agreement', 'admin') that can significantly impact token supply and individual balances (7.4 Economic). For… |
| **Upgrades** | 1/10 | High | The SuperToken utilizes the UUPS proxy pattern, allowing for future upgrades of its logic (7.7 Upgrades). The `updateCode` and `changeAdmin` functions are restricted to the 'admin' role, providing… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 54.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `CD-03` — Critical Vulnerability: Anyone Can Initialize or Destroy Upgradeable Logic  *(Severity: Critical · Status: Unresolved)*

The implementation contract, which contains the core logic for the SuperToken, is not adequately protected. Functions such as `burn`, `castrate`, `disableYieldBackend`, `downgrade`, `downgradeTo`, `enableYieldBackend`, `initialize`, and `initializeWithAdmin` can be called by *anyone* on the implementation contract directly. This allows an attacker to potentially re-initialize the contract, disable critical features, or even destroy its state, leading to severe disruption or loss of funds.

**Recommendation:** This is a critical security flaw. The contract developers must immediately ensure that the implementation contract's `initialize` and other sensitive functions are protected from external calls, typically by using an `initializer` modifier that prevents re-initialization and by ensuring that the implementation contract cannot be directly interacted with after deployment, except through the proxy. This usually involves deploying the implementation contract in an uninitialized state and never cal…


### `CD-02` — Uninitialized State Variable Could Lead to Unexpected Behavior  *(Severity: High · Status: Unresolved)*

The `getAccountActiveAgreements` function attempts to use a state variable that has not been explicitly initialized with a starting value. This could lead to the function operating with a default or unexpected value, potentially causing incorrect logic or errors in how active agreements are retrieved.

**Recommendation:** The contract developers should ensure that all state variables are properly initialized before being used. This involves reviewing the `getAccountActiveAgreements` function and its dependencies to set a clear initial value for any uninitialized variables.


### `CP-02` — Privileged Address Can Directly Alter Token Balances  *(Severity: High · Status: Unresolved)*

The 'self' controller has the power to directly reduce the balance of any token holder by calling the `selfBurn` function. This allows the controller to burn tokens from any targeted address, effectively moving them out of the holder's control without their consent.

**Recommendation:** Token holders should understand that the 'self' controller possesses significant power over individual token balances. Verify the security and trustworthiness of the 'self' controller, as it can unilaterally burn tokens from any account.


### `CP-01` — Privileged Addresses Can Create New Tokens  *(Severity: Medium · Status: Unresolved)*

The 'host' or 'self' controller has the ability to increase the total supply of SuperTokens by calling functions like `selfMint`, `upgrade`, `upgradeTo`, `downgrade`, `downgradeTo`, `operationUpgrade`, `operationDowngrade`, and `operationUpgradeTo`. This means new tokens can be generated, which could dilute the value of existing token holdings.

**Recommendation:** Token holders should be aware that the 'host' or 'self' controller can mint new tokens. Ensure that these controllers are highly trusted and that their operational procedures are robust to prevent unauthorized or excessive minting.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0x0deb…c75f — holds 54.3% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 24% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CD-01` — Potential for Minor Value Loss Due to Calculation Order  *(Severity: Low · Status: Unresolved)*

The `_toUnderlyingAmount` function performs a division operation before a multiplication. In Solidity, integer division truncates any remainder, which can lead to a small loss of precision or value if the division occurs before the multiplication that would have preserved the value.

**Recommendation:** While often minor, this issue can result in small discrepancies. The contract developers should review the `_toUnderlyingAmount` function to ensure calculations are ordered to minimize or eliminate any rounding losses, typically by performing multiplication before division where possible.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 67.8% of supply. What remains: 13.1% in wallets, 54.7% in other contracts. 51,377 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Superfluid (SUP), market cap $1M, rank #2705. Traded on Coinbase. 51,377 holders. Verified by: exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $273K (DexScreener, all pools). 24h trading volume $161K (CoinGecko, all markets, daily snapshot). 24h trading volume $111K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0639 on 2025-12-07; the price is now 94.0135% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-7 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $273K of DEX liquidity across 5 pools. Launch: 316 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa69f...8792`](https://basescan.org/address/0xa69f80524381275a7ffdb3ae01c54150644c8792) |
| **Network** | Base |
| **Price** | $0.003851 |
| **24h Volume** | $74.0K |
| **Liquidity** | $66.7K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 67.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2568 buys / 2705 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xc4838fbeef72ba0719a4c4f1efeec68991b74a20)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/superfluid-token-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-29*
