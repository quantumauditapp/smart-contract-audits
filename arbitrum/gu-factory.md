---
token: GU Factory
ticker: GU
network: arbitrum
risk_score: 89
status: critical
date: 2026-09-15
---

# GU Factory (GU) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 89/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gu-factory-arb)

---

## Audit Summary

The GuCoin contract implements an ERC-20 token with LayerZero OFT capabilities, integrating with a bonding curve and liquidity manager. It features an automatic LP seeding mechanism and a fee distribution model. The contract exhibits a high degree of centralization, relying heavily on external contracts and privileged roles for critical operations like token minting, burning, and initial liquidity provisioning. Several potential economic and technical risks have been identified, primarily stemming from centralized control, reliance on external contract integrity, and specific implementation details that could lead to operational issues or front-running opportunities.

> **Final Recommendation:** Thoroughly audit all external contracts (`IGuBondingCurve`, `IGuLiquidityManager`, `IGuFactory`) that `GuCoin` interacts with, as their security directly impacts the `GuCoin` system. Consider implementing a timelock or multi-signature wallet for the `owner()` role and potentially for the `bondingCurve` if it has administrative functions, to mitigate risks associated with centralized control.
Review the `_seedLP` mechanism for potential front-running vectors and ensure the `RESERVE_TOKEN` is compatible with the `_transferReserveExact` function, especially if it's a fee-on-transfer token, to prevent operational failures.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The GuCoin contract demonstrates a well-structured design, inheriting from OFT and Ownable, and utilizing SafeERC20 for secure token interactions. The implementation includes robust checks like… |
| **Governance / Economics** | 1/10 | High | The economic model incorporates virtual reserves, initial supply, and a maximum supply, alongside protocol and creator fees, demonstrating a structured approach to tokenomics (7.4 Economic). The… |
| **Upgrades** | 3/10 | High | The GuCoin contract itself is not designed for upgradeability, as indicated by `is_proxy: false` and the absence of proxy patterns. This reduces the risk of upgrade-related vulnerabilities for this… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control over Critical Functions  *(Severity: High · Status: Unresolved)*

The `mint` and `burnCurve` functions are exclusively callable by the `bondingCurve` contract, granting it significant control over the GuCoin token supply. If the `bondingCurve` contract is compromised or contains vulnerabilities, it could lead to unauthorized minting or burning, impacting the token's economic stability. Additionally, the `_seedLP` function, which initializes liquidity and distributes a substantial portion of the reserve token balance, automatically transfers funds to the `creator` and `owner()` (protocol owner). This centralizes control over initial liquidity distribution and involves large value transfers to privileged addresses, posing a single point of failure risk (7.3…

**Recommendation:** Implement a multi-signature wallet or a timelock for the `owner()` address to manage protocol fees and for any administrative functions within the `bondingCurve` contract. This would introduce a delay or require multiple approvals for critical operations, reducing the risk of a single point of compromise. Ensure the `bondingCurve` contract itself undergoes rigorous security audits.


### `M-01` — Potential for Front-Running in _seedLP Trigger  *(Severity: Medium · Status: Unresolved)*

The `_seedLP` function is triggered internally when `totalSupply()` reaches `MAX_SUPPLY` after a `mint` operation. The address that performs the final `mint` to push the supply over `MAX_SUPPLY` becomes the `caller` in `_seedLP` and receives a portion of the `CREATOR_FEE` (`reserveTokenBalance * CREATOR_FEE / 20_000`). An attacker could monitor the `totalSupply()` and front-run the transaction that would trigger `_seedLP`, ensuring they are the `caller` and thus receiving a fee. While the amount might be small, it represents an unnecessary incentive for front-running and potential for unfair distribution (7.4 Economic).

**Recommendation:** Re-evaluate the mechanism for distributing the `CREATOR_FEE` portion to the `caller` in `_seedLP`. Consider distributing this portion to a neutral address (e.g., the `creator` or `owner`) or removing this specific incentive to prevent front-running. Alternatively, ensure the `_seedLP` function is only callable by a trusted entity after `MAX_SUPPLY` is reached, rather than being automatically triggered by any `mint`.


### `M-02` — Incompatibility with Fee-on-Transfer Reserve Tokens  *(Severity: Medium · Status: Unresolved)*

The `_transferReserveExact` function, used for distributing fees and seeding LP, includes a strict check: `if (reserveToken.balanceOf(to) != recipientBalance + amount) { revert InvalidReserveBalance(); }`. If the `RESERVE_TOKEN` is a fee-on-transfer token (which deducts a percentage from the transferred amount), the recipient will receive slightly less than `amount`. Consequently, this check will always fail, causing the transaction to revert. This would prevent the `_seedLP` function from completing successfully, effectively blocking the token's launch and liquidity provisioning, and also preventing any subsequent fee distributions that rely on this function (7.2 Code Security, 7.4 Economi…

**Recommendation:** Clarify in the documentation that the `RESERVE_TOKEN` must not be a fee-on-transfer token. If fee-on-transfer tokens are intended to be supported, modify the `_transferReserveExact` function to account for potential transfer fees, for example, by checking `reserveToken.balanceOf(to) >= recipientBalance + amount - tolerance` or by simply removing the strict equality check if the exact amount received is not critical for protocol logic.


### `M-03` — High Reliance on External Contracts  *(Severity: Medium · Status: Unresolved)*

The `GuCoin` contract heavily relies on the correct and secure functioning of several external contracts, including `IGuBondingCurve`, `IGuLiquidityManager`, and `IGuFactory`. For instance, `price()` depends on `IGuBondingCurve.getAmountOutSell`, and initial liquidity provisioning is handled by `IGuLiquidityManager.createAndInitializePool` and `seedLP`. The `FACTORY` contract determines critical addresses like `LIQUIDITY_MANAGER` and `harvester`. Any vulnerability, misconfiguration, or malicious upgrade in these external contracts could directly impact the `GuCoin` token's functionality, value, and overall system integrity (7.1 Architecture, 7.6 External).

**Recommendation:** Ensure all external contracts (`IGuBondingCurve`, `IGuLiquidityManager`, `IGuFactory`) undergo comprehensive security audits. Implement robust monitoring for these external contracts, especially if they are upgradeable, to detect any suspicious activity or changes. Clearly document the expected behavior and security assumptions regarding these dependencies.


### `L-01` — Potential `accReserve` Desynchronization  *(Severity: Low · Status: Unresolved)*

The `accReserve` variable is an internal accounting mechanism for the reserve, incremented during `mint` and decremented during `burnCurve`. While `mint` includes a check against the actual `RESERVE_TOKEN` balance, `accReserve` could become desynchronized from the actual `RESERVE_TOKEN` balance held by the `GuCoin` contract if `RESERVE_TOKEN` is transferred to or from the `GuCoin` contract outside of the `mint` or `burnCurve` functions (e.g., accidental transfers). This desynchronization could lead to `TVL()` misrepresenting the actual backing of the token (7.2 Code Security, 7.4 Economic).

**Recommendation:** Consider adding a mechanism for a privileged role (e.g., `owner()`) to reconcile `accReserve` with the actual `RESERVE_TOKEN` balance, or to recover accidentally sent `RESERVE_TOKEN`s. Alternatively, ensure that the contract's design strictly prevents any external transfers of `RESERVE_TOKEN` to or from the `GuCoin` contract outside of its intended functions.


### `I-01` — Immutability of Key Parameters  *(Severity: Informational · Status: Unresolved)*

Many critical parameters such as `FACTORY`, `POSITION_MANAGER`, `LIQUIDITY_MANAGER`, `RESERVE_TOKEN`, `VIRTUAL_BALANCE`, `INITIAL_SUPPLY`, `MAX_SUPPLY`, `PROTOCOL_FEE`, `CREATOR_FEE`, `COMMUNITY_FEE_RATIO`, `creator`, `bondingCurve`, and `lp` are declared as `immutable`. This design choice provides strong guarantees about the system's core configuration, preventing malicious changes post-deployment (7.1 Architecture). However, it also means that if any of these parameters are set incorrectly during deployment, they cannot be changed, potentially leading to a permanent malfunction or loss of funds.

**Recommendation:** Ensure extremely thorough testing and verification of all constructor parameters before deployment to production environments. Consider a multi-stage deployment or a 'dry run' on a testnet to confirm all immutable parameters are set correctly according to the protocol's specifications.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xff3e...533f`](https://arbiscan.io/address/0xff3e87789b668e177a4e9a3d1b75e74b5155533f) |
| **Network** | Arbitrum |
| **Price** | $0.004421 |
| **24h Volume** | $211.9K |
| **Liquidity** | $39.0K |
| **Volume / Liquidity** | 5.4× |
| **Token Age** | 2d |
| **Top-10 Holders** | 75.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 360 buys / 286 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0xa0fe0c8bfff15bc4ab4988eb86761c9d10d34170)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gu-factory-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-15*
