---
token: Yooldo Games
ticker: ESPORTS
network: bsc
risk_score: 42
status: medium
date: 2026-07-24
---

# Yooldo Games (ESPORTS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/yooldo-games-bsc)

---

## Audit Summary

The YooldoToken contract is an ERC20 token built on OpenZeppelin standards, incorporating burnable, pausable, permit, and voting functionalities. It introduces custom logic for freezing/unfreezing accounts. The contract exhibits strong technical security due to its reliance on audited libraries, but presents medium economic and governance risks due to the high degree of centralized control held by the owner, despite the use of a multisig.

> **Final Recommendation:** Implement a timelock for all critical owner-controlled functions, such as `pause`, `unpause`, `freezeAccount`, `unfreezeAccount`, and `transferOwnership`. This will provide a delay for sensitive operations, enhancing transparency and allowing users to react to proposed changes. Additionally, ensure the multisig wallet controlling the `Ownable` address is secured with robust operational procedures and strong key management practices to mitigate the risks associated with centralized control.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract `YooldoToken` is built upon battle-tested OpenZeppelin ERC20 standards, including `ERC20Burnable`, `ERC20Pausable`, `ERC20Permit`, and `ERC20Votes`. The implementation correctly… |
| **Governance / Economics** | 4/10 | Medium | The token design grants significant centralized control to the `Ownable` address, which is configured as a multisig (7.3 Access Control). The owner can pause all token transfers, freeze individual… |
| **Upgrades** | 7/10 | Low | The `YooldoToken` contract is not designed to be upgradeable (7.7 Upgrades), meaning its logic is immutable once deployed. This eliminates risks associated with proxy patterns, such as storage… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 31.1% |
| **Top-3 Unlocked** | 61.2% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control by Owner  *(Severity: High · Status: Unresolved)*

The `Ownable` contract grants significant power to a single address (or multisig) to control critical token functionalities. The owner can `pause` all token transfers, `freezeAccount` or `unfreezeAccount` any address, and `burn` tokens. While the use of a multisig mitigates some risk, a compromise or malicious act by the owner could severely impact token functionality, user funds, and the overall ecosystem (7.3 Access Control, 7.4 Economic, 7.8 Operations).

**Recommendation:** While centralization is a design choice for this token, consider implementing a multi-signature wallet with a high threshold for the owner address. Additionally, explore community governance mechanisms for critical decisions in the future. Ensure robust security practices for the owner's private keys or multisig setup.


### `M-01` — Lack of Timelock for Critical Operations  *(Severity: Medium · Status: Unresolved)*

Critical owner-controlled functions such as `pause`, `unpause`, `freezeAccount`, `unfreezeAccount`, and `transferOwnership` can be executed immediately by the owner. The absence of a timelock means there is no delay for sensitive operations, preventing users from reacting to potentially malicious or erroneous actions and reducing transparency (7.3 Access Control, 7.5 Governance, 7.8 Operations).

**Recommendation:** Implement a timelock mechanism for all critical owner-controlled functions. This would introduce a mandatory delay between the owner initiating an action and its actual execution, providing a window for review and reaction by the community or other stakeholders.


### `L-01` — Unused Modifier `notFrozen`  *(Severity: Low · Status: Unresolved)*

The `notFrozen` modifier is defined in the `YooldoToken` contract but is not utilized in any function. The logic for checking frozen accounts is directly implemented within the `_update` function. While this does not introduce a vulnerability, the presence of an unused modifier can lead to confusion and suggests potential for code cleanup or refactoring (7.2 Code Security).

**Recommendation:** Remove the unused `notFrozen` modifier to improve code clarity and maintainability, or integrate it into relevant functions if its intended use was overlooked. The current implementation in `_update` is correct and sufficient.


### `I-01` — Non-Upgradeable Contract  *(Severity: Informational · Status: Unresolved)*

The `YooldoToken` contract is deployed directly and does not implement an upgrade mechanism (e.g., proxy pattern). This means the contract's logic is immutable once deployed to the blockchain. While this avoids upgrade-related complexities and risks, it implies that any future bug fixes, feature enhancements, or changes to the token's core logic would necessitate deploying a new contract and migrating the token supply, which can be a complex and disruptive process (7.7 Upgrades).

**Recommendation:** Acknowledge the immutability of the contract. For future projects requiring flexibility, consider using an upgradeable proxy pattern (e.g., UUPS) to allow for future logic updates without requiring a token migration. For this contract, ensure thorough testing before deployment given its immutability.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf39e...8e48`](https://bscscan.com/address/0xf39e4b21c84e737df08e2c3b32541d856f508e48) |
| **Network** | BNB Chain |
| **Price** | $0.02637 |
| **24h Volume** | $43.8K |
| **Liquidity** | $994.2K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 85.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1697 buys / 3075 sells |

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

### Is Yooldo Games a scam?

Based on automated analysis, Yooldo Games scores 67/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Yooldo Games safe to buy?

Our scanner flagged a risk score of 67/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Yooldo Games been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x5bb59bb9371cbec158ed602d5f3cf1ad1c9b4462)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/yooldo-games-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-24*
