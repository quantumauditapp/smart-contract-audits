---
token: Worldcoin
ticker: WLD
network: ethereum
risk_score: 66
status: high
date: 2026-06-10
---

# Worldcoin (WLD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/worldcoin-eth)

---

## Audit Summary

The WLD token contract implements a standard ERC20 token with additional logic for initial supply distribution and a controlled inflation mechanism. It leverages OpenZeppelin's Ownable2Step for robust ownership management. While the core token functionality and access controls are well-implemented, the centralized nature of the owner and minter roles, coupled with the complexity of the inflation logic, introduces notable risks. The contract is not upgradeable via proxy, simplifying its architecture but requiring new deployments for any future changes.

> **Final Recommendation:** To enhance the security and decentralization of the WLD token, consider implementing a multi-signature wallet or a robust governance system for the `owner` and `minter` roles. This would distribute control and require multiple approvals for critical operations, mitigating the risks associated with centralized power. Additionally, ensure all stakeholders have a clear and comprehensive understanding of the inflation mechanism's nuances to prevent misinterpretations regarding token supply dynamics.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The WLD token contract demonstrates good technical quality, utilizing battle-tested OpenZeppelin libraries for ERC20 and Ownable2Step functionalities, which enhances code security (7.2 Code… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a high degree of centralization, primarily through the `owner` and `minter` roles (7.3 Access Control, 7.5 Governance). The owner can perform a one-time mint up to… |
| **Upgrades** | 5/10 | Medium | The WLD contract is implemented as a standard, non-upgradeable token contract. It does not utilize proxy patterns (e.g., UUPS, Transparent) for upgradeability (7.7 Upgrades). This design choice… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralization Risk with Owner and Minter Roles  *(Severity: High · Status: Unresolved)*

The `owner` role, secured by `Ownable2Step`, holds significant power, including a one-time mint of up to `INITIAL_SUPPLY_CAP` and the ability to set/change the `minter` address. The `minter` then controls all subsequent inflation minting. If these roles are controlled by a single EOA, it introduces a high degree of centralization and a single point of failure, potentially leading to unauthorized supply manipulation or governance issues. (7.3 Access Control, 7.4 Economic, 7.5 Governance)

**Recommendation:** Consider implementing a multi-signature wallet or a robust governance mechanism (e.g., a DAO) to control the `owner` and `minter` roles. This would distribute control and require multiple approvals for critical operations, enhancing security and decentralization.


### `M-01` — Complex Inflation Logic and Potential for Misinterpretation  *(Severity: Medium · Status: Unresolved)*

The `mintInflation` function implements a detailed inflation mechanism with `inflationUnlockTime`, `inflationCapPeriod`, and `inflationCapWad`. The NatSpec explicitly notes that 'it is possible for period over period inflation to reach up to (1 + inflation cap)^2 - 1' under certain conditions. While documented, this complexity could lead to misinterpretation by stakeholders regarding the actual maximum inflation rate over arbitrary periods, potentially causing unexpected token supply increases. (7.2 Code Security, 7.4 Economic)

**Recommendation:** Ensure comprehensive documentation and clear communication to all stakeholders about the nuances of the inflation mechanism, especially the potential for slightly higher-than-expected inflation over certain intervals. Consider adding internal helper functions or clearer comments if the logic can be further modularized for readability.


### `L-01` — Immutability of Critical Constructor Parameters  *(Severity: Low · Status: Unresolved)*

Several critical parameters, including `inflationCapPeriod`, `inflationCapWad`, and `inflationUnlockTime`, are set as `immutable` during contract deployment via the constructor. Additionally, the initial `existingHolders` and `existingAmounts` are processed only at deployment. Any error or misconfiguration in these parameters during deployment cannot be corrected post-deployment, requiring a new contract deployment and migration if a mistake occurs. (7.1 Architecture, 7.8 Operations)

**Recommendation:** Thoroughly review and test all constructor parameters in a controlled environment before mainnet deployment. Implement robust deployment scripts and verification processes to minimize the risk of misconfiguration. While immutability provides certainty, ensure the initial setup is flawless.


### `I-01` — Lack of Event for Minter Address Update  *(Severity: Informational · Status: Unresolved)*

The `setMinter` function allows the contract owner to update the `minter` address, which is a critical role responsible for inflation minting. However, this function does not emit an event upon a successful update. This lack of an event makes it challenging for off-chain monitoring systems, block explorers, and users to track changes to the `minter` address, reducing transparency and auditability. (7.2 Code Security, 7.8 Operations)

**Recommendation:** Add an event to the `setMinter` function, such as `event MinterUpdated(address indexed oldMinter, address indexed newMinter);`, to log changes to the `minter` address. This will improve transparency and allow for easier tracking and auditing of this critical role.

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
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
