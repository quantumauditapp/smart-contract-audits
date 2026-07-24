---
token: MineBean
ticker: BEAN
network: base
risk_score: 82
status: critical
date: 2026-07-23
---

# MineBean (BEAN) — Smart Contract Security Analysis | Base

> **Risk Score: 82/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/minebean-base)

---

## Audit Summary

The MineBean contract is an ERC20 token with a capped supply, a minter role, and an integrated Time-Weighted Average Price (TWAP) oracle based on Uniswap V4. The audit identified a critical misconfiguration risk in the TWAP oracle's price calculation, high centralization risks due to owner privileges, and potential vulnerabilities related to the TWAP window and transfer restrictions. While the contract leverages well-audited OpenZeppelin and Uniswap V4 libraries, the custom logic for oracle configuration and transfer controls introduces significant security concerns that require immediate attention.

> **Final Recommendation:** Address the critical `beanIsToken0` misconfiguration in `setPoolId` by dynamically determining or validating the token order. Implement robust access control mechanisms, such as a multi-signature wallet or time-locks, for sensitive owner-controlled functions to mitigate centralization risks. Re-evaluate the TWAP oracle's window size and snapshot interval to enhance its resilience against manipulation. Clarify and refine the `_isBean` whitelist logic to ensure it aligns with intended token utility and user experience.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract utilizes robust OpenZeppelin ERC20 and Uniswap V4 libraries for core functionalities (7.2 Code Security). The TWAP oracle mechanism incorporates a `MIN_SNAPSHOT_INTERVAL` to prevent… |
| **Governance / Economics** | 6/10 | Medium | The contract implements a `MAX_SUPPLY` and a `minter` role, providing a controlled token issuance mechanism (7.4 Economic). The owner can `freezeMinter` and `removeLimits`, which are one-way actions… |
| **Upgrades** | 6/10 | Medium | The contract is not designed as an upgradeable proxy. Therefore, it does not introduce any upgrade-specific risks (7.7 Upgrades). Any changes to the contract's logic would require a new deployment… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 98.4% — GoPlus SafeToken Locker |
| **Top-1 Unlocked Holder** | 0.9% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 3 Medium · 🟢 1 Low_

### `C-01` — Incorrect `beanIsToken0` Assignment in `setPoolId`  *(Severity: Critical · Status: Unresolved)*

The `setPoolId` function, which configures the Uniswap V4 pool for TWAP calculations, unconditionally sets `beanIsToken0 = false`. This assumes that the Bean token will always be `token1` in any configured pool. If the actual pool created via `PoolManager.initialize()` has Bean as `token0`, the `getTWAPAmountOut` function will perform an inverted price calculation, leading to severe economic exploits, incorrect pricing, and potential loss of funds for users or protocols relying on this oracle.

**Recommendation:** The `beanIsToken0` flag must be correctly determined based on the actual `PoolKey` provided. Modify `setPoolId` to compare `address(this)` with `_poolId.token0` or `_poolId.token1` to accurately set `beanIsToken0`. For example: `beanIsToken0 = address(this) == _poolId.token0;`.


### `H-01` — High Centralization Risk via Owner Privileges  *(Severity: High · Status: Unresolved)*

The contract uses the `Ownable` pattern, granting the deployer (owner) exclusive control over critical functions such as `setMinter`, `freezeMinter`, `removeLimits`, and `setPoolId`. A compromised owner key or a malicious owner could lead to unauthorized minting (by setting a malicious minter), disabling essential transfer restrictions, or misconfiguring the core oracle, posing a single point of failure and significant trust risk.

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the owner address to require multiple approvals for critical operations. For highly sensitive functions like `freezeMinter` or `removeLimits`, explore integrating a time-lock mechanism or a decentralized governance process to introduce a delay and community oversight.


### `H-02` — Short TWAP Window Susceptible to Manipulation  *(Severity: High · Status: Unresolved)*

The `getOracleTWAP` function calculates the Time-Weighted Average Price using a simple arithmetic mean of only 5 tick snapshots. While `MIN_SNAPSHOT_INTERVAL` (6 blocks) provides some delay between updates, a short window of 5 snapshots makes the TWAP more susceptible to manipulation. An attacker could potentially influence a significant portion of the snapshots within a relatively short period, leading to a manipulated TWAP price that could be exploited by dependent protocols.

**Recommendation:** Increase the number of snapshots used for the TWAP calculation (e.g., 10-20 or more) to provide a longer averaging window, making manipulation more costly and difficult. Additionally, evaluate if a longer `MIN_SNAPSHOT_INTERVAL` or a more robust averaging method (e.g., weighted average, median) would enhance resilience against price attacks.


### `M-01` — Irreversible `removeLimits` Function  *(Severity: Medium · Status: Unresolved)*

The `removeLimits` function, callable by the owner, permanently sets the `limited` flag to `false`. This action is irreversible and disables the `require(_isBean[to] \|\| _isBean[from], "Not Allowed");` check within the `_update` function. This restriction is intended to control transfers involving AMM pools. Removing this limit permanently could have unintended consequences if the project's long-term strategy requires re-enabling such controls or if the initial restriction was critical for specific economic models.

**Recommendation:** If the `limited` flag is intended to be a configurable setting that might need to be toggled, consider making it reversible. If it is a one-time transition, ensure that the implications of permanently removing this restriction are fully understood, documented, and align with the project's long-term vision. Clearly communicate this irreversible action to users and stakeholders.


### `M-02` — Ambiguous `_isBean` Whitelist in `_update`  *(Severity: Medium · Status: Unresolved)*

The `_update` override includes a conditional `require(_isBean[to] \|\| _isBean[from], "Not Allowed");` when `limited` is true and neither `from` nor `to` is excluded. The `_isBean` mapping is populated only once during the constructor with a fixed list of addresses. This design implies that only explicitly whitelisted 'Bean' addresses or excluded addresses can interact with AMM pools when `limited` is true. This could lead to unexpected transfer failures for legitimate users who are not on these lists, hindering liquidity provision, trading, or general token utility.

**Recommendation:** Clarify the exact purpose and scope of the `_isBean` whitelist. If it's intended to restrict AMM interactions, ensure that all legitimate participants (e.g., liquidity providers, traders) can be added to this list or that the restriction is clearly communicated. Consider if this restriction is truly necessary or if it introduces unnecessary friction and complexity for users.


### `M-03` — TWAP Not Ready for Extended Periods  *(Severity: Medium · Status: Unresolved)*

The `getOracleTWAP` function reverts with `TWAPNotReady` if fewer than 5 snapshots have been recorded. If AMM interactions (transfers to/from the pool) are infrequent or the `MIN_SNAPSHOT_INTERVAL` is too long, the TWAP oracle might not be ready for extended periods. This could prevent dependent protocols from functioning correctly, accessing a reliable price feed, or executing critical operations that rely on the TWAP.

**Recommendation:** Assess the expected frequency of AMM interactions and adjust `MIN_SNAPSHOT_INTERVAL` and the number of required snapshots accordingly to ensure the TWAP is consistently available. Consider implementing a fallback mechanism or a grace period for protocols consuming the TWAP, or allow for a TWAP calculation with fewer than 5 snapshots (e.g., using the available average) if the staleness risk is acceptable for the use case.


### `L-01` — Gas Inefficiency in `_updateTickSnapshot` Trigger  *(Severity: Low · Status: Unresolved)*

The `_updateTickSnapshot` function is triggered on every transfer to or from an AMM pool via the `_update` override. While `MIN_SNAPSHOT_INTERVAL` prevents actual state updates frequently, the `block.number` check and the `extsload` call to `poolManager.getSlot0(poolId)` still execute on every such transfer. The `extsload` operation can be gas-intensive, potentially adding unnecessary gas costs to AMM-related transfers even when no snapshot update occurs.

**Recommendation:** Evaluate the gas cost impact of the `extsload` call on every AMM interaction. If significant, consider optimizing the trigger condition for `_updateTickSnapshot` to only call `getSlot0` when a snapshot update is actually due, or explore alternative mechanisms for updating snapshots, such as a dedicated keeper bot, to offload this cost from user transactions.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5c72...5a5d`](https://basescan.org/address/0x5c72992b83e74c4d5200a8e8920fb946214a5a5d) |
| **Network** | Base |
| **Price** | $2.8100 |
| **24h Volume** | $29.0K |
| **Liquidity** | $251.8K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 86.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 239 buys / 1364 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xd7e5522c9cc3682c960afada6adde0f8116580f2ad2cef08c197faf625e53842)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/minebean-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-23*
