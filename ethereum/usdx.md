---
token: USDx
ticker: USDX
network: ethereum
risk_score: 8
status: low
date: 2026-09-05
---

# USDx (USDX) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usdx-eth)

---

## Audit Summary

The USDx contract, an upgradeable ERC-20 token, implements standard functionalities with additional access control, pausing, and blacklisting features. The contract leverages OpenZeppelin's upgradeable libraries, ensuring robust architecture and upgrade safety. While the implementation is technically sound, the inherent centralization through privileged roles presents significant governance and economic risks, particularly concerning the control over minting, burning, and user funds.

> **Final Recommendation:** It is crucial to ensure that all privileged roles, especially the `DEFAULT_ADMIN_ROLE`, are assigned to robust, multi-signature wallets or time-locked governance contracts to mitigate the risks associated with centralized control. Implement comprehensive monitoring for all role-based actions and token supply changes. Users should be fully aware of the inherent centralization and the capabilities of the privileged roles, particularly regarding pausing and blacklisting functionalities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract demonstrates strong technical foundations (7.1 Architecture, 7.2 Code Security). It correctly utilizes OpenZeppelin's upgradeable ERC-20, ERC-20Permit, and AccessControl libraries… |
| **Governance / Economics** | 9/10 | Low | The USDx token's economic model (7.4 Economic) is inherently centralized, typical for a managed stablecoin. Privileged roles (`MARKET_ROLE`, `BRIDGE_ROLE`) have the ability to mint tokens, and… |
| **Upgrades** | 8/10 | Low | The contract is designed for upgradeability using the TransparentUpgradeableProxy pattern (7.7 Upgrades). It correctly inherits from `Initializable` and includes a `__gap` storage variable to prevent… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Timelock |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 1 Low · ⚪ 9 Informational_

### `L-01` — Potential for `approve` Front-running  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The standard ERC-20 `approve` function is susceptible to a known front-running vulnerability. If a user approves an amount for a spender, and then attempts to approve a different amount, a malicious actor can front-run the second `approve` transaction by spending the initially approved amount. When the second `approve` transaction confirms, the spender will have access to the sum of both approved amounts, potentially leading to unintended fund transfers.

**Recommendation:** Advise users to set `approve` amounts to zero before increasing them, or to use the `increaseAllowance` and `decreaseAllowance` functions (if available, though not explicitly implemented in this contract beyond `ERC20Upgradeable`'s internal `_approve`). The `permit` function, which includes a `deadline`, offers better protection against this specific front-running vector.


### `I-01` — Unused Constant `AxisV2Ids.VERSION`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `AxisV2Ids.VERSION` constant is imported from `AxisV2Ids.sol` but is not utilized anywhere within the `USDx` contract. While this does not pose a security vulnerability, it represents dead code.

**Recommendation:** Remove the import or the constant if it is not intended for use within this contract to improve code clarity and reduce unnecessary dependencies.


### `I-02` — Centralized Control and Single Point of Failure  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` in the `USDx` contract holds extensive power, including the ability to grant and revoke all other roles (`MARKET_ROLE`, `BRIDGE_ROLE`, `RESTRICTION_ROLE`, `PAUSER_ROLE`). If this role's private key or controlling entity is compromised, an attacker could gain full control over the token's supply (via minting/burning roles), pause all operations, and blacklist any address, leading to a complete compromise of the protocol and user funds. While the proxy admin is a Timelock, the `admin` for the contract's internal roles needs to be equally robust.

**Recommendation:** Ensure that the `DEFAULT_ADMIN_ROLE` is controlled by a robust governance mechanism, such as a multi-signature wallet with a high threshold or a time-locked governance contract. Avoid assigning this role to a single External Owned Account (EOA). Regularly review and audit the security of the entities holding these privileged roles.


### `I-03` — Blacklist and Pause Functionality Risks  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract includes `pause()` and `blacklist()` functionalities, controlled by the `PAUSER_ROLE` and `RESTRICTION_ROLE` respectively. These functions allow privileged entities to halt all token transfers and approvals, or to prevent specific addresses from interacting with the token. While intended for emergency response or regulatory compliance, these features introduce a significant centralization risk, enabling potential censorship, denial of service for users, or freezing of funds at the discretion of the role holders.

**Recommendation:** Clearly communicate the existence and implications of these functionalities to all users. Implement strict operational procedures and multi-party control for the `PAUSER_ROLE` and `RESTRICTION_ROLE` to prevent misuse. Consider adding a time-lock or governance vote requirement for activating these critical functions, if feasible within the protocol's design.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 40.9% in wallets, 59.0% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Axis USD (USDX), market cap $67M, rank #360. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $2.0M (DexScreener, all pools). 24h trading volume $4.1M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Stablecoin — yield-bearing  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Stablecoins. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $2.0M of DEX liquidity across 1 pools. Launch: 3 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa1fa...33f8`](https://etherscan.io/address/0xa1fa7777974312f7d801a8880714a218f76233f8) |
| **Network** | Ethereum |
| **Price** | $0.9988 |
| **24h Volume** | $4.13M |
| **Liquidity** | $2.01M |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 3d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 110 buys / 201 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xe521ba88837b2726e5343cca91ada6f19f356c45)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usdx-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-05*
