---
token: Broccoli
ticker: BROCCOLI
network: bsc
risk_score: 10
status: low
date: 2026-09-25
---

# Broccoli (BROCCOLI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/broccoli-bsc-9502)

---

## Audit Summary

The TokenV2 contract is an upgradeable ERC20 token utilizing OpenZeppelin's upgradeable libraries. It implements transfer constraints that initially prevent interaction with specified Uniswap V2 and V3 pools, which can be removed by the contract owner. While the architecture is standard and leverages well-audited components, significant centralization risks exist regarding initial token distribution and the owner's control over transfer restrictions. The contract is designed for upgradeability via a proxy pattern.

> **Final Recommendation:** To mitigate the identified risks, it is strongly recommended to implement robust operational security measures for the owner's address, such as using a multi-signature wallet. Clear communication and transparency regarding the project's plans for initial token distribution and the conditions under which transfer constraints will be removed are crucial for building trust and preventing potential market manipulation. Consider implementing a time-lock or a community-driven governance mechanism for critical functions like `removeTransferConstraints` to decentralize control over time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract demonstrates good technical practices by inheriting from OpenZeppelin's battle-tested upgradeable ERC20, ERC20Permit, and Ownable contracts (7.2 Code Security). It correctly uses the… |
| **Governance / Economics** | 6/10 | Medium | The economic model presents a significant centralization risk as all `maxSupply` tokens are minted to the initializer address, concentrating 100% of the supply initially (7.4 Economic). Furthermore… |
| **Upgrades** | 10/10 | Low | The contract is designed for upgradeability using the UUPS proxy pattern, leveraging OpenZeppelin's upgradeable contracts and the `initializer` modifier (7.7 Upgrades). The `constructor` is correctly… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 76.3% — UNCX Locker |
| **Top-1 Unlocked Holder** | 23.7% |
| **Top-3 Unlocked** | 23.7% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Initial Token Distribution Centralization  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). During the `initialize` function, all `maxSupply` tokens are minted directly to `msg.sender`. This results in 100% of the token's total supply being held by a single address immediately after deployment. While this is a common pattern for initial supply, it creates a high centralization risk for token distribution and potential for market manipulation if the initial holder's actions are not transparent or well-managed.

**Recommendation:** Provide clear documentation and transparency regarding the project's plans for distributing the initial token supply. Consider implementing a vesting schedule or a decentralized distribution mechanism (e.g., airdrops, liquidity mining programs) to gradually decentralize token ownership and reduce the risk of concentrated holdings impacting market stability.


### `M-02` — Centralized Control Over Transfer Constraints  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `owner` address has the sole authority to call `removeTransferConstraints()`, which permanently disables the restrictions on transferring tokens to and from the specified Uniswap V2 and V3 pools. This gives the owner significant, unilateral control over the token's liquidity and market dynamics, potentially allowing them to enable/disable trading on major DEXs at will. A compromised owner key or malicious owner could severely impact the token's market.

**Recommendation:** Consider implementing a multi-signature wallet for the owner address to control critical functions like `removeTransferConstraints()`. Alternatively, introduce a time-lock mechanism for this function, allowing a grace period for users to react before changes take effect. For long-term decentralization, explore integrating a community-driven governance mechanism to manage such critical parameters.


### `L-01` — Immutable Pool Addresses and MetaURI  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `uniswapV2Pool`, `uniswapV3Pool`, and `metaURI` variables are set only during the `initialize` function and lack any setter functions. This makes these parameters immutable after deployment. While immutability can be a security feature, it means that if the specified pool addresses become outdated, incorrect, or if the `metaURI` needs to be updated (e.g., for branding or metadata changes), an upgrade of the entire contract implementation would be required.

**Recommendation:** Assess whether these parameters truly need to be immutable. If flexibility is desired, consider adding `onlyOwner` setter functions for `metaURI` and potentially for the pool addresses, especially if the project anticipates changes in liquidity pool infrastructure or metadata requirements. Ensure any such setters are protected by appropriate access controls.


### `I-01` — Missing `_authorizeUpgrade` in UUPS Implementation  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `TokenV2` contract is an upgradeable implementation using the UUPS pattern but does not include an `_authorizeUpgrade` function. This means that the decision and authorization for upgrading the contract are solely managed by the proxy's admin/owner, without any additional checks or logic within the implementation contract itself. While this is a valid design choice, some projects implement `_authorizeUpgrade` to add specific checks (e.g., governance votes, time-locks) before an upgrade can proceed.

**Recommendation:** This is an informational finding. If the current design aligns with the project's security and governance model, no action is strictly required. However, for enhanced security and decentralized control over upgrades, consider adding an `_authorizeUpgrade` function to the implementation contract that integrates with a governance mechanism or a time-lock, ensuring upgrades are not solely dependent on a single administrative key.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x23d3...8f2b`](https://bscscan.com/address/0x23d3f4eaaa515403c6765bb623f287a8cca28f2b) |
| **Network** | BNB Chain |
| **Price** | $0.001622 |
| **24h Volume** | $86.0K |
| **Liquidity** | $214.8K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 94.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 473 buys / 178 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xc18caa1658b91076425c8d287ca1b8e238344bfe)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/broccoli-bsc-9502)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-25*
