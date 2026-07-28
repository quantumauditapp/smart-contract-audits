---
token: Espresso
ticker: ESP
network: ethereum
risk_score: 64
status: high
date: 2026-07-27
---

# Espresso (ESP) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 64/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/espresso-eth)

---

## Audit Summary

The audit covers the `EspTokenV2` contract, an upgradeable ERC20 token utilizing the UUPS proxy pattern. The contract introduces a `mint` function restricted to a designated `rewardClaim` address. Overall, the contract demonstrates good security practices, leveraging OpenZeppelin's upgradeable standards and a Timelock for ownership. Key areas of focus include the centralization risk associated with the `rewardClaim` and the specific storage layout strategy employed.

> **Final Recommendation:** It is crucial to thoroughly audit the `RewardClaim` contract, as its security directly impacts the `EspTokenV2` supply. Implement robust monitoring for the `rewardClaim` address and ensure its operational security. For future upgrades, strictly adhere to the 'frozen-inheritance pattern' for storage layout to prevent critical storage collisions. Consider adding explicit `__gap` arrays to custom contracts as a defensive measure, even with the current pattern, to provide additional buffer against potential storage layout changes or deviations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture (7.1) utilizes the UUPS proxy pattern with OpenZeppelin's upgradeable contracts, ensuring a robust foundation. Code security (7.2) is generally strong, with proper use of… |
| **Governance / Economics** | 3/10 | High | The economic model (7.4) centers on an ERC20 token with a minting mechanism controlled by a `rewardClaim` contract. This introduces a significant centralization risk (H-01), as the security of the… |
| **Upgrades** | 1/10 | High | The contract employs the UUPS upgradeability pattern (7.7), with `_authorizeUpgrade` correctly restricted to the owner. The project explicitly uses a 'frozen-inheritance pattern' for storage layout… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralization Risk of `rewardClaim` for Token Supply  *(Severity: High · Status: Unresolved)*

The `mint` function, which controls the total supply of `EspTokenV2`, is solely accessible by the `rewardClaim` address. If the `rewardClaim` contract or the private key controlling it is compromised, an attacker could mint an arbitrary amount of tokens, leading to severe inflation and devaluation of the token. The security of the entire token ecosystem heavily relies on the security and integrity of the `rewardClaim` entity.

**Recommendation:** Implement robust security measures for the `rewardClaim` contract, including thorough audits, multi-signature control, and potentially a time-lock for critical actions. Consider mechanisms to pause minting in emergencies or to cap the total mintable supply over time. Ensure the `rewardClaim` contract itself has strong access control and is not susceptible to common vulnerabilities.


### `M-01` — Reliance on 'Frozen-Inheritance Pattern' for Storage Layout  *(Severity: Medium · Status: Unresolved)*

The contract explicitly states it uses a 'frozen-inheritance pattern' where new state variables are only added in new child contracts that inherit from previous versions. While this is a valid approach to managing upgradeable storage, it is less common than using `__gap` arrays. This pattern requires strict adherence across all future upgrades. Any deviation, such as adding a new state variable to an existing parent contract in a future version, would lead to storage collisions and critical vulnerabilities.

**Recommendation:** Maintain strict discipline in future upgrades by always appending new state variables only in new child contracts. Document this pattern clearly for all developers working on the project. Consider adding a linter or static analysis tool to enforce this pattern during development. While not strictly necessary with this pattern, adding explicit `__gap` arrays to custom contracts could provide an additional layer of safety against accidental storage collisions.


### `L-01` — Unknown Security Posture of `rewardClaim` Contract  *(Severity: Low · Status: Unresolved)*

The `rewardClaim` address, which has the exclusive privilege to mint tokens, is set during `initializeV2`. The security and functionality of the contract at this address are unknown. If `rewardClaim` points to a contract that is not properly secured (e.g., lacks access control, is self-destructible, or has vulnerabilities), it could indirectly expose the `EspTokenV2` to risks.

**Recommendation:** Ensure that the `rewardClaim` address points to a thoroughly audited and securely managed contract. The `RewardClaim` contract should have robust access control, be non-upgradable or securely upgradable, and ideally be controlled by a multi-signature wallet or a governance mechanism with a time-lock. Document the expected behavior and security requirements for the `rewardClaim` contract.


### `I-01` — Missing `__gap` Arrays in Custom Contracts  *(Severity: Informational · Status: Unresolved)*

The custom contracts `EspToken` and `EspTokenV2` do not include explicit `__gap` arrays, despite using OpenZeppelin's upgradeable contracts which do. While the project explicitly states a 'frozen-inheritance pattern' where new variables are only appended in child contracts, `__gap` arrays are a standard defensive measure in upgradeable contracts to explicitly reserve storage slots and prevent accidental collisions if the storage layout of parent contracts (including OpenZeppelin's) changes or if the 'frozen-inheritance' pattern is ever inadvertently broken.

**Recommendation:** Consider adding `__gap` arrays to `EspToken` and `EspTokenV2` to explicitly reserve storage slots. This provides an additional layer of safety and makes the storage layout more resilient to potential future changes or deviations from the 'frozen-inheritance pattern'. For example, `uint256[50] private __gap;` could be added at the end of each custom contract.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x031d...db9a`](https://etherscan.io/address/0x031de51f3e8016514bd0963d0b2ab825a591db9a) |
| **Network** | Ethereum |
| **Price** | $0.08953 |
| **24h Volume** | $317.6K |
| **Liquidity** | $392.5K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 91.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 380 buys / 344 sells |

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

## Frequently Asked Questions

### Is Espresso a scam?

Based on automated analysis, Espresso scores 65/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Espresso safe to buy?

Our scanner flagged a risk score of 65/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Espresso been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x1d301bfd44ddd5b1095a11f079854cedb17a8812b73433992f50e06215e6a06e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/espresso-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-27*
