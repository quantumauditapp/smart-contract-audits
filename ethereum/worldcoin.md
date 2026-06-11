---
token: Worldcoin
ticker: WLD
network: ethereum
risk_score: 100
status: critical
date: 2026-06-10
---

# Worldcoin (WLD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/worldcoin-eth)

---

## Audit Summary

The WLD token contract implements an ERC20 token with an initial supply cap and a controlled inflation mechanism. The contract utilizes OpenZeppelin's Ownable2Step for robust ownership management and includes explicit checks for input validation and supply caps. Key findings include the complexity and potential for higher-than-stated effective inflation rates in certain scenarios, and the significant centralized control over token supply by the owner and minter roles. While the code quality is high, these economic and governance risks warrant careful consideration.

> **Final Recommendation:** The WLD contract is technically sound, leveraging established libraries and adhering to good coding practices. However, the high degree of centralized control over token supply and the complex inflation mechanics introduce significant economic and governance risks. It is strongly recommended to implement multi-signature wallets for critical roles (owner, minter) and ensure transparent communication regarding the inflation model's nuances.

For enhanced security and operational resilience, consider a Premium Deploy option. This would involve deploying the contract through a battle-tested multi-signature wallet (e.g., Gnosis Safe) for the owner role, and potentially integrating with a robust monitoring solution to track supply changes and minter activities in real-time.

## Security Analysis

The WLD token contract implements an ERC20 token with an initial supply cap and a controlled inflation mechanism. The contract utilizes OpenZeppelin's Ownable2Step for robust ownership management and includes explicit checks for input validation and supply caps. Key findings include the complexity and potential for higher-than-stated effective inflation rates in certain scenarios, and the significant centralized control over token supply by the owner and minter roles. While the code quality is high, these economic and governance risks warrant careful consideration.

The WLD contract is technically sound, leveraging established libraries and adhering to good coding practices. However, the high degree of centralized control over token supply and the complex inflation mechanics introduce significant economic and governance risks. It is strongly recommended to implement multi-signature wallets for critical roles (owner, minter) and ensure transparent communication regarding the inflation model's nuances.

For enhanced security and operational resilience, consider a Premium Deploy option. This would involve deploying the contract through a battle-tested multi-signature wallet (e.g., Gnosis Safe) for the owner role, and potentially integrating with a robust monitoring solution to track supply changes and minter activities in real-time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The WLD contract demonstrates strong technical foundations (7.1 Architecture, 7.2 Code Security). It inherits from battle-tested OpenZeppelin contracts (ERC20, Ownable2Step), ensuring standard complia |
| **Governance / Economics** | 6/10 | High | The contract design presents significant governance and economic considerations (7.4 Economic, 7.5 Governance). The owner has substantial power, including a one-time initial mint up to 10 billion toke |
| **Upgrades** | 6/10 | Low | The WLD contract is not designed as an upgradeable proxy (7.7 Upgrades). Its logic is immutable once deployed, meaning no upgrade safety issues are present. Any future changes to the token's core logi |

## Security Findings

_🟠 2 High · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Inflation Rate Exceeds Stated Cap in Edge Cases  *(Severity: High · Status: Unresolved)*

The `mintInflation` function's logic, as acknowledged in the contract's own documentation, allows for the effective inflation rate over certain periods to exceed the `inflationCapWad` (up to `(1 + inflation cap)^2 - 1`). This means that while a nominal inflation cap is defined, the actual token supply dilution experienced by holders could be higher than a simple interpretation of the `inflationCapWad` might suggest, potentially leading to unexpected economic outcomes.

**Recommendation:** Ensure all public-facing documentation, whitepapers, and communications clearly explain this nuanced behavior of the inflation mechanism, providing concrete examples of how the effective inflation rate can vary. Consider adding monitoring tools to track actual inflation rates and compare them against expected values. If possible, explore alternative inflation mechanisms that provide a stricter, more predictable cap over any given period.


### `H-02` — Centralized Control over Token Supply  *(Severity: High · Status: Unresolved)*

The contract grants significant power to the `owner` and subsequently to the `minter` address. The `owner` can perform a one-time mint up to `INITIAL_SUPPLY_CAP` (10 billion tokens) and then designate an arbitrary `minter`. The `minter` can then continuously mint new tokens, subject only to the inflation rules. This high degree of centralized control over the token supply introduces a significant trust assumption and potential single point of failure if the owner or minter keys are compromised or misused, or if the roles are maliciously exercised.

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for both the `owner` and `minter` roles to distribute control and reduce the risk of a single point of compromise. Consider a time-locked mechanism for critical actions like `setMinter` to allow for community review or emergency intervention, enhancing transparency and security.


### `L-01` — Immutability of Inflation Unlock Time  *(Severity: Low · Status: Unresolved)*

The `inflationUnlockTime` is set once in the constructor based on `inflationLockPeriod_ + block.timestamp` and cannot be modified thereafter. While this provides predictability, it removes flexibility to adjust the inflation start time in response to unforeseen market conditions, regulatory changes, or governance decisions. This immutability could become a limitation if the project requires adaptive economic parameters in the future.

**Recommendation:** If future flexibility is desired, consider adding a governance-controlled mechanism (e.g., via a DAO or a multi-sig) to adjust the `inflationUnlockTime` within predefined bounds, or to pause/unpause inflation. If immutability is a strict design choice, ensure this is clearly communicated to all stakeholders as a core property of the token's economic model.


### `I-01` — Non-Renounceable Ownership  *(Severity: Informational · Status: Unresolved)*

The `renounceOwnership` function is explicitly overridden to revert, preventing the owner from ever relinquishing control of the contract. This is a deliberate design choice to ensure continuous oversight and prevent accidental or malicious renunciation of the owner role, which is critical given the owner's extensive powers.

**Recommendation:** This is a design decision. No action is required unless the project's long-term decentralization strategy changes. Ensure this design choice is well-documented and understood by all stakeholders, highlighting that ownership will always reside with the designated address(es).

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x163f...8753`](https://etherscan.io/address/0x163f8c2467924be0ae7b5347228cabf260318753) |
| **Network** | Ethereum |
| **Price** | $0.4144 |
| **24h Volume** | $283.0K |
| **Liquidity** | $277.1K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 2y |
| **Top-10 Holders** | 69.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 293 buys / 263 sells |

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

## Frequently Asked Questions

### Is Worldcoin a scam?

Based on the provided data, Worldcoin (WLD) exhibits several risk factors commonly associated with potential scams, though this analysis doesn't definitively label it one. The critical concerns include ownership not being renounced, extreme token centralization with 69.7% in top 10 holders, and unlocked liquidity. These factors create significant avenues for malicious action or market instability, warranting extreme caution from investors.

### Is Worldcoin safe to buy?

Investing in Worldcoin (WLD) carries a critical risk, indicated by its 75/100 risk score, making it unsafe for risk-averse investors. Key safety concerns include the unrenounced contract ownership, allowing the deployer control. The vast majority of tokens (69.7%) are concentrated in the top 10 wallets, posing a high centralization risk. Furthermore, unlocked liquidity means funds could be withdrawn, impacting market stability significantly.

### Has Worldcoin been audited?

The provided data confirms that the Worldcoin (WLD) contract is verified on Ethereum, meaning its code is publicly available for inspection. However, contract verification is not the same as a comprehensive security audit by an independent third party. The data provided does not explicitly state whether Worldcoin has undergone a formal security audit. Investors should seek audit reports if available.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x841820459769cd629b10a36fd12e603938cc2679)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/worldcoin-eth)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
