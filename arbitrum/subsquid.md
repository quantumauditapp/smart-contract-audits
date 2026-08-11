---
token: Subsquid
ticker: SQD
network: arbitrum
risk_score: 52
status: high
date: 2026-08-11
---

# Subsquid (SQD) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 52/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/subsquid-arb)

---

## Audit Summary

The SQD token contract is an ERC20 implementation based on OpenZeppelin's battle-tested library, deployed on Arbitrum. It includes specific functions for bridging (`bridgeMint`, `bridgeBurn`) controlled by an immutable `l2Gateway` address. While the contract's technical implementation is robust and follows best practices, the centralized control over token supply by the `l2Gateway` introduces a significant external dependency risk, elevating the overall risk profile.

> **Final Recommendation:** Prioritize the security and operational integrity of the `l2Gateway` contract, as it is the single point of control for the SQD token supply. Implement robust monitoring, multi-signature controls, and a comprehensive incident response plan for the `l2Gateway` to detect and mitigate any unauthorized activity promptly. Educate users about the inherent risks of bridged assets and the reliance on the bridge's security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The SQD token contract leverages the OpenZeppelin ERC20 standard, providing a robust and well-audited foundation (7.2 Code Security). Access control for bridge-specific minting and burning functions… |
| **Governance / Economics** | 1/10 | High | The economic security of the SQD token is heavily reliant on the `l2Gateway` contract, which possesses the exclusive ability to mint and burn tokens (7.4 Economic). This centralized control, while… |
| **Upgrades** | 6/10 | Medium | The SQD contract is not designed with an upgrade mechanism (e.g., proxy pattern), meaning its code is immutable after deployment (7.7 Upgrades). This eliminates risks associated with upgradeability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 93.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control of Token Supply via L2 Gateway (External Dependency Risk)  *(Severity: High · Status: Unresolved)*

The `l2Gateway` address has exclusive control over the `bridgeMint` and `bridgeBurn` functions, allowing it to arbitrarily increase or decrease the token supply. While this is a necessary design for a bridged token, it introduces a single, highly privileged point of control. The security of the entire SQD token's economic integrity on Arbitrum is directly dependent on the security and integrity of the `l2Gateway` contract. A compromise of the `l2Gateway` would lead to a critical economic impact, such as hyperinflation or complete draining of the token supply.

**Recommendation:** Implement the highest security standards for the `l2Gateway` contract, including robust access control (e.g., multi-signature wallet), thorough auditing, and continuous monitoring. Establish a clear and secure operational procedure for managing the `l2Gateway` to minimize the risk of compromise. Consider decentralizing control over time if feasible for the bridge architecture.


### `L-01` — ERC20 `approve` Race Condition  *(Severity: Low · Status: Unresolved)*

The standard ERC20 `approve` function is susceptible to a known race condition. If a user approves an amount, and then approves a different amount before the first transaction is mined, an attacker could front-run the second approval to spend the original approved amount, and then the second approval would overwrite the allowance, potentially allowing the attacker to spend more than intended. This is an inherent characteristic of the ERC20 standard and not a flaw in the OpenZeppelin implementation.

**Recommendation:** Inform users about this potential race condition. Recommend a 'set-to-zero then approve' pattern for changing allowances, where users first approve 0 and then the new amount. Alternatively, consider using ERC20 permit or a custom `increaseAllowance`/`decreaseAllowance` pattern if the token design allows for it, although OpenZeppelin's `_spendAllowance` mitigates some risks.


### `I-01` — Use of `unchecked` Blocks for Addition  *(Severity: Informational · Status: Unresolved)*

The `_update` function, specifically for `_totalSupply += value` and `_balances[to] += value`, utilizes `unchecked` blocks. In Solidity 0.8.0 and later, arithmetic operations revert on overflow/underflow by default. `unchecked` blocks disable this check. While this is a standard optimization in OpenZeppelin contracts, and `uint256` provides a vast range, a theoretical overflow could occur if `value` is extremely large and the target variable is near `type(uint256).max`, leading to a wrap-around instead of a revert.

**Recommendation:** No direct action is required as this is a standard and generally safe optimization in modern Solidity for operations where overflow is highly improbable. However, it's important to be aware of this design choice and ensure that the context of `value` in `_mint` and `_burn` operations does not introduce an unexpected overflow scenario.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1337...8ab1`](https://arbiscan.io/address/0x1337420ded5adb9980cfc35f8f2b054ea86f8ab1) |
| **Network** | Arbitrum |
| **Price** | $0.04422 |
| **24h Volume** | $622.5K |
| **Liquidity** | $379.8K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 2y |
| **Top-10 Holders** | 57.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2142 buys / 1458 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0xc24b560c7f8a1a50c2336cd8917af61b5e14984f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/subsquid-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
