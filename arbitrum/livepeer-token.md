---
token: Livepeer Token
ticker: LPT
network: arbitrum
risk_score: 63
status: high
date: 2026-07-27
---

# Livepeer Token (LPT) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 63/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/livepeer-token-arb)

---

## Audit Summary

The LivepeerToken contract is an ERC20 token implementation leveraging OpenZeppelin's battle-tested libraries for core functionality, including access control, burning, and permit functionality. The contract introduces specific roles for minting and burning tokens, managed by a `DEFAULT_ADMIN_ROLE`. While the code quality is high and standard vulnerabilities are mitigated by the Solidity version and library usage, the centralized control over token supply via these roles presents a significant operational and economic risk if the administrative keys are compromised. The contract is not upgradeable, ensuring immutability but requiring new deployments for any future changes.

> **Final Recommendation:** To mitigate the identified risks, it is strongly recommended to secure the `DEFAULT_ADMIN_ROLE` with a robust multi-signature wallet solution, ideally with a high threshold for execution. Consider implementing time-locks for critical administrative actions, such as granting or revoking roles, to provide a window for community oversight and emergency intervention. Regularly review and audit the addresses holding critical roles to ensure their continued security and trustworthiness.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The LivepeerToken contract demonstrates strong technical foundations (7.1 Architecture, 7.2 Code Security). It utilizes OpenZeppelin's `AccessControl`, `ERC20Burnable`, and `ERC20Permit` modules… |
| **Governance / Economics** | 1/10 | High | The contract's economic model (7.4 Economic) and governance structure (7.5 Governance) are highly centralized. The `DEFAULT_ADMIN_ROLE` has the power to grant and revoke `MINTER_ROLE` and… |
| **Upgrades** | 3/10 | High | The LivepeerToken contract is not designed with upgradeability in mind (7.7 Upgrades). It is a standard, immutable contract deployment. This design choice ensures that the contract's logic cannot be… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control over Token Supply  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` has ultimate control over the token's supply by being able to grant and revoke both `MINTER_ROLE` and `BURNER_ROLE`. A compromise of the `DEFAULT_ADMIN_ROLE` would allow an attacker to mint an arbitrary amount of tokens, leading to hyperinflation, or burn all tokens, causing a denial of service for the token's utility. This centralization is a significant single point of failure for the token's economic stability (7.3 Access Control, 7.4 Economic, 7.5 Governance).

**Recommendation:** Implement a robust multi-signature wallet for the `DEFAULT_ADMIN_ROLE` with a high number of required confirmations. Consider distributing the signers across different trusted entities. Explore decentralized governance mechanisms for critical role management in the long term.


### `M-01` — Single Point of Failure for Admin Role Management  *(Severity: Medium · Status: Unresolved)*

If the `DEFAULT_ADMIN_ROLE` is controlled by a single External Owned Account (EOA), it represents a single point of failure. The compromise of this EOA's private key would grant an attacker full control over the token's administrative functions, including the ability to assign themselves `MINTER_ROLE` or `BURNER_ROLE` (7.8 Operations).

**Recommendation:** Ensure that the `DEFAULT_ADMIN_ROLE` is controlled by a multi-signature wallet (e.g., Gnosis Safe) rather than a single EOA. This significantly increases the security posture by requiring multiple approvals for critical operations.


### `L-01` — Lack of Time-Locks for Critical Operations  *(Severity: Low · Status: Unresolved)*

The contract does not implement time-locks for critical administrative actions, such as granting or revoking roles, or for large minting operations. While not a direct vulnerability, the absence of time-locks means that administrative changes or significant supply alterations can be executed immediately, leaving no window for community review or emergency intervention in case of a compromised key (7.8 Operations).

**Recommendation:** Consider integrating a time-lock mechanism for sensitive administrative functions. This would introduce a delay between the initiation and execution of critical operations, allowing for detection and potential mitigation of malicious actions.


### `I-01` — Non-Upgradeability of Contract  *(Severity: Informational · Status: Unresolved)*

The LivepeerToken contract is deployed as a standard, non-upgradeable contract. This means its logic cannot be modified after deployment. While this provides immutability and reduces the risk of malicious upgrades, it also implies that any future bug fixes, feature enhancements, or protocol changes would require deploying a new contract and migrating all existing token holders, which can be a complex and disruptive process (7.7 Upgrades).

**Recommendation:** Acknowledge the implications of non-upgradeability. For future contracts, if flexibility is desired, consider implementing an upgradeable proxy pattern (e.g., UUPS or Transparent Proxy) from OpenZeppelin. For this contract, ensure robust testing and a clear migration plan if changes become necessary.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x289b...a839`](https://arbiscan.io/address/0x289ba1701c2f088cf0faf8b3705246331cb8a839) |
| **Network** | Arbitrum |
| **Price** | $1.4200 |
| **24h Volume** | $142.8K |
| **Liquidity** | $213.4K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 4y |
| **Top-10 Holders** | 98.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1191 buys / 1300 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Livepeer Token a scam?

Based on automated analysis, Livepeer Token scores 67/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Livepeer Token safe to buy?

Our scanner flagged a risk score of 67/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Livepeer Token been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0x4fd47e5102dfbf95541f64ed6fe13d4ed26d2546)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/livepeer-token-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-27*
