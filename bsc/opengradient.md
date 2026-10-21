---
token: OpenGradient
ticker: OPG
network: bsc
risk_score: 67
status: high
date: 2026-09-21
---

# OpenGradient (OPG) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/opengradient-bsc)

---

## Audit Summary

The OpenGradientOFT contract is an Omnichain Fungible Token (OFT) built on LayerZero v2, inheriting from LayerZero's OFT and OpenZeppelin's Ownable contracts. The contract's logic is minimal, primarily relying on battle-tested external libraries. The primary risks are associated with the owner's centralized control over LayerZero configurations and the inherent dependency on the LayerZero protocol's security. The owner is a 2/3 multisig, which mitigates some centralization risks.

> **Final Recommendation:** Ensure the private keys controlling the 2/3 multisig owner address are secured with the highest industry standards, as this address holds significant control over the token's cross-chain functionality. Implement robust operational procedures (7.8 Operations) for all LayerZero configuration changes, including multi-party review and time-locks if feasible, to prevent unauthorized or erroneous updates. Regularly monitor the LayerZero protocol for any security announcements or vulnerabilities, as the contract's security is directly dependent on its external dependencies (7.6 External).

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The OpenGradientOFT contract is a straightforward implementation of an Omnichain Fungible Token (OFT) using LayerZero v2. It leverages well-audited OpenZeppelin `Ownable` and LayerZero `OFT` base… |
| **Governance / Economics** | 1/10 | High | The contract's economic model (7.4 Economic) is that of a standard fungible token, with its value derived from external factors not within the contract's scope. Governance (7.5 Governance) is… |
| **Upgrades** | 6/10 | Medium | The OpenGradientOFT contract is not designed to be upgradeable (7.7 Upgrades), as it does not implement any proxy pattern. This eliminates all risks associated with upgradeability, such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 67.8% |
| **Top-3 Unlocked** | ⚠️ 98.4% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 3 Informational_

### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

The contract inherits from OpenZeppelin's `Ownable` contract, granting the deployer-designated owner significant control over critical LayerZero configurations. The owner can call functions like `setTrustedRemoteAddress`, `setMinDstGas`, and `setDelegate` on the underlying OFT contract. While the owner is a 2/3 multisig, a compromise of the multisig's keys could lead to unauthorized configuration changes, potentially disrupting cross-chain transfers or leading to loss of funds.

**Recommendation:** While the use of a multisig mitigates some risk, consider implementing a time-lock mechanism for critical administrative actions. This would introduce a delay between the initiation and execution of sensitive operations, allowing time for detection and intervention in case of a malicious or erroneous transaction. Additionally, ensure robust key management practices for the multisig signers.


### `L-01` — Non-Upgradeable Contract  *(Severity: Low · Status: Unresolved)*

The OpenGradientOFT contract is deployed as a standard, non-upgradeable contract. This means that its logic cannot be modified after deployment. While this eliminates risks associated with upgrade mechanisms (e.g., proxy vulnerabilities), it also means that any discovered bugs or desired feature enhancements would necessitate a new contract deployment and a potentially complex token migration process.

**Recommendation:** This is a design choice. If future upgradeability is desired, a proxy pattern (e.g., UUPS or Transparent) should be considered during the initial design phase. For the current non-upgradeable design, ensure thorough testing and auditing to minimize the likelihood of needing future changes.


### `I-01` — Heavy Dependency on LayerZero v2 Protocol  *(Severity: Informational · Status: Unresolved)*

The `OpenGradientOFT` contract is built upon LayerZero v2's `OFT` contract, making it entirely dependent on the security, correctness, and operational integrity of the LayerZero protocol and its associated endpoints. Any vulnerabilities, misconfigurations, or operational failures within the LayerZero infrastructure could directly impact the functionality and security of the OpenGradientOFT token, potentially leading to frozen assets or incorrect cross-chain transfers.

**Recommendation:** Maintain continuous monitoring of LayerZero's security announcements, audits, and operational status. Establish clear procedures for responding to potential LayerZero-related incidents. Diversify cross-chain solutions if the project's risk tolerance allows for it, or ensure a robust incident response plan is in place for LayerZero-specific issues.


### `I-02` — Constructor Delegate as Owner  *(Severity: Informational · Status: Unresolved)*

In the constructor, the `_delegate` address is used for both initializing the `OFT` base contract (as the LayerZero delegate) and the `Ownable` base contract (as the contract owner). This design choice ensures that the same entity controls both the LayerZero-specific delegate functions and the general contract ownership functions.

**Recommendation:** This is a consistent design choice. Ensure that the chosen `_delegate` address (which is a multisig in this case) is highly secure and trusted, as it holds comprehensive control over the token's administrative and cross-chain functionalities.


### `I-03` — Fixed Token Name and Symbol  *(Severity: Informational · Status: Unresolved)*

The token's `NAME` ('OpenGradient') and `SYMBOL` ('OPG') are declared as `private constant` variables within the contract. This means they are immutable and cannot be changed after deployment.

**Recommendation:** This is standard and expected behavior for ERC-20 compliant tokens. No action is required unless there was an explicit requirement for these properties to be mutable.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5fec...cb9d`](https://bscscan.com/address/0x5feccd17c393caf1001d18164236a37e731fcb9d) |
| **Network** | BNB Chain |
| **Price** | $0.1397 |
| **24h Volume** | $53.9K |
| **Liquidity** | $21.2K |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 92.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 869 buys / 756 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x0a4b571c4932d84de11a6bca96bb9ba5bf27ff1c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/opengradient-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-21*
