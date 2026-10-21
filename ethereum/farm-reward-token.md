---
token: FARM Reward Token
ticker: FARM
network: ethereum
risk_score: 71
status: high
date: 2026-09-12
---

# FARM Reward Token (FARM) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 71/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/farm-reward-token-eth)

---

## Audit Summary

The RewardToken contract implements a standard ERC20 token with minting capabilities and a supply cap. It utilizes OpenZeppelin's SafeMath for arithmetic safety and a MinterRole for access control over minting. The contract exhibits good adherence to the ERC20 standard and incorporates a supply cap to prevent unlimited inflation. However, the role management for minters presents significant centralization and operational risks, potentially leading to loss of minting functionality or unrecoverable state. The use of an older Solidity compiler version is also noted.

> **Final Recommendation:** It is strongly recommended to implement a more robust and decentralized access control mechanism for critical roles, particularly the MinterRole. This could involve allowing the contract owner to manage minters or requiring multi-signature approval for role changes. Additionally, consider upgrading the Solidity compiler version to a more recent and actively supported release to benefit from the latest security features and optimizations. Establish clear operational procedures for managing the MinterRole to prevent accidental loss of minting capability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates good technical security practices (7.2 Code Security) by using SafeMath for all arithmetic operations, effectively mitigating integer overflow/underflow vulnerabilities. It… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4 Economic) includes a supply cap, which is a positive control against excessive inflation. However, the governance and access control (7.3 Access Control, 7.5 Governance) for… |
| **Upgrades** | 3/10 | High | The contract is not designed with an upgrade mechanism (7.7 Upgrades) such as a proxy pattern. Therefore, it is not upgradeable, which eliminates upgrade-related risks but means any discovered… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 60.5% |
| **Top-3 Unlocked** | ⚠️ 89.6% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Minter Role Management and Single Point of Failure  *(Severity: High · Status: Unresolved)*

The `MinterRole` is highly centralized, with the `addMinter` function only callable by an existing minter. There is no mechanism for the contract owner or any other designated role to add or remove minters. This creates a single point of failure: if the initial minter's private key is lost, compromised, or if the last minter renounces their role without assigning another, the ability to mint new tokens (up to the defined cap) could be permanently lost or fall into malicious hands. This poses a significant operational risk and could lead to an unrecoverable state for the token's minting functionality.

**Recommendation:** Implement a more robust role management system. Consider allowing the contract owner to add and remove minters, or integrate a multi-signature wallet for managing the MinterRole. This would distribute control and reduce the risk associated with a single point of failure. A timelock for critical role changes could also be considered.


### `M-01` — Renounce Minter Leads to Potential Loss of Minting Capability  *(Severity: Medium · Status: Unresolved)*

The `renounceMinter` function allows any address holding the MinterRole to remove themselves. If the last remaining minter calls this function without first assigning another minter, the contract will enter a state where no address holds the `MinterRole`. In this scenario, the `mint` function will become permanently unusable, preventing any further token issuance, even if the supply cap has not been reached.

**Recommendation:** Implement a safeguard within the `renounceMinter` function to prevent the last minter from renouncing their role. This could involve checking `_minters.count()` (if a counter is added) or requiring that at least one other minter exists before allowing a minter to renounce. Alternatively, ensure strict operational procedures are in place to manage minter roles.


### `L-01` — Older Solidity Compiler Version  *(Severity: Low · Status: Unresolved)*

The contract is compiled with Solidity version `^0.5.0`. While `SafeMath` is used to mitigate integer overflows, older compiler versions may contain known bugs, lack certain security features, or be less optimized compared to more recent and actively maintained versions (e.g., 0.8.x).

**Recommendation:** Consider upgrading the contract to a more recent and actively supported Solidity compiler version (e.g., 0.8.x). This would allow the contract to benefit from the latest bug fixes, security enhancements (such as native overflow checks), and gas optimizations.


### `I-01` — Missing Dedicated Event for `_burnFrom`  *(Severity: Informational · Status: Unresolved)*

The internal `_burnFrom` function performs a token burn and an allowance update. While the underlying `_burn` and `_approve` calls emit `Transfer` and `Approval` events respectively, there is no dedicated event specifically for the `_burnFrom` action. A distinct event could provide clearer and more granular off-chain visibility for this specific operation, aiding in monitoring and auditing.

**Recommendation:** Consider adding a dedicated event, such as `BurnFrom(address indexed account, address indexed spender, uint256 amount)`, within the `_burnFrom` function. This would enhance transparency and provide a clearer audit trail for tokens burned on behalf of another address.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa024...a14d`](https://etherscan.io/address/0xa0246c9032bc3a600820415ae600c6388619a14d) |
| **Network** | Ethereum |
| **Price** | $7.1300 |
| **24h Volume** | $113.9K |
| **Liquidity** | $47.3K |
| **Volume / Liquidity** | 2.4× |
| **Token Age** | 6y |
| **Top-10 Holders** | 69.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 375 buys / 469 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x56feaccb7f750b997b36a68625c7c596f0b41a58)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/farm-reward-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
