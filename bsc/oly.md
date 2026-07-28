---
token: OLY
ticker: OLY
network: bsc
risk_score: 56
status: high
date: 2026-07-27
---

# OLY (OLY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 56/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/oly-bsc)

---

## Audit Summary

The OLY token contract implements a custom ERC20 token with a fee mechanism on trades involving a main liquidity pair. It utilizes OpenZeppelin's AccessControl for role-based permissions. The contract exhibits a high degree of centralization, with critical functions controlled by a single admin role, and introduces a potential Denial of Service vector through an external call to the fee receiver.

> **Final Recommendation:** Implement a multi-signature wallet or time-lock for the `DEFAULT_ADMIN_ROLE` to manage critical functions and parameters, enhancing security and decentralization. Introduce a robust error handling mechanism or a pull-based system for external calls to the `feeReceiver` to mitigate Denial of Service risks. Consider adopting battle-tested OpenZeppelin ERC20 contracts for improved security and maintainability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements a custom ERC20 token with `SafeMath` for arithmetic safety. A complex fee mechanism is integrated into the `_transfer` function, applying different ratios for buy and sell… |
| **Governance / Economics** | 3/10 | High | The protocol exhibits high centralization, with the `DEFAULT_ADMIN_ROLE` possessing extensive control over critical parameters such as `mainPair`, `feeRatio`, and `buyFeeRatio`, as well as role… |
| **Upgrades** | 4/10 | Medium | The contract is not designed with an upgradeability pattern (e.g., proxy). Any future changes to the contract logic would require a complete redeployment and a potentially complex token migration… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 2 High · 🟡 3 Medium · 🟢 1 Low_

### `H-01` — Denial of Service via Malicious or Faulty `feeReceiver`  *(Severity: High · Status: Unresolved)*

The `_transfer` function makes an external call to `IFeeReceiver(feeReceiver).triggerSwapFeeForLottery()` when tokens are sold to `mainPair` and fees are taken. If the `feeReceiver` contract is malicious and reverts, or if it is a buggy contract that runs out of gas, all such token transfers will fail. This effectively creates a Denial of Service (DoS) vulnerability for a significant portion of token trades, blocking users from selling their tokens.

**Recommendation:** Implement a robust error handling mechanism for the external call, such as a `try/catch` block to gracefully handle reverts without blocking transfers. Alternatively, consider a pull-based system where the `feeReceiver` initiates the call, or implement an emergency mechanism to disable the external call or change the `feeReceiver` address if it becomes problematic.


### `H-02` — Centralized Control and Single Point of Failure  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE`, initially assigned to the contract deployer, possesses extensive control over critical contract parameters and roles. This includes the ability to set `mainPair`, adjust `feeRatio` and `buyFeeRatio`, and grant/revoke `MINT` and `INTERN_SYSTEM` roles. A compromise of this single administrative address would allow an attacker to manipulate fees, disable minting/burning controls, or block trades, leading to severe financial and operational risks.

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) or a time-lock contract to manage the `DEFAULT_ADMIN_ROLE`. This adds a layer of security by requiring multiple approvals for critical operations and provides a delay for users to react to proposed changes.


### `M-01` — Custom ERC20 Implementation Risk  *(Severity: Medium · Status: Unresolved)*

The contract utilizes a custom implementation of the ERC20 standard rather than leveraging battle-tested and widely audited libraries like OpenZeppelin's `ERC20`. While `SafeMath` is used, custom implementations are more prone to subtle bugs, edge-case vulnerabilities, or non-compliance issues that might be overlooked during development and testing, potentially leading to unexpected behavior or exploits.

**Recommendation:** Consider refactoring the token contract to inherit from OpenZeppelin's `ERC20` contract. If a custom implementation is strictly necessary, ensure comprehensive unit and integration tests are developed and executed to cover all ERC20 functionalities and potential edge cases thoroughly.


### `M-02` — Lack of Emergency Pause Mechanism  *(Severity: Medium · Status: Unresolved)*

The contract lacks a mechanism to pause critical operations (such as transfers or fee collection) in the event of an emergency. In scenarios like a discovered vulnerability, a malicious `feeReceiver`, or a compromised `mainPair`, the absence of a pause function could lead to irreversible losses, continued exploitation, or prolonged protocol disruption.

**Recommendation:** Implement a pause mechanism, for example, by inheriting from OpenZeppelin's `Pausable` contract. This mechanism should be controllable by a trusted entity (e.g., the `DEFAULT_ADMIN_ROLE` or a multi-sig) to temporarily halt operations during emergencies, allowing time for remediation.


### `M-03` — Potential for Fee Manipulation by Admin  *(Severity: Medium · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` has the authority to change `feeRatio` and `buyFeeRatio` at any time via the `setRatio` function. While this provides flexibility, it also allows an administrator to arbitrarily increase fees up to `PRECISION` (100%) without prior notice or community consensus. Such sudden changes could negatively impact user trust, token utility, and overall protocol stability.

**Recommendation:** Implement a time-lock for changes to critical parameters like `feeRatio` and `buyFeeRatio`. This would introduce a delay between the proposal and activation of a change, providing transparency and allowing users to react or voice concerns. Alternatively, integrate these parameter changes into a broader governance mechanism.


### `L-01` — `INTERN_SYSTEM` Role Misconfiguration Risk  *(Severity: Low · Status: Unresolved)*

The `INTERN_SYSTEM` role is designed to exempt addresses from trading fees when interacting with the `mainPair`. While the constructor correctly grants this role to the deployer and `_feeReceiver`, accidental granting of this role to the `mainPair` address itself could lead to unintended fee bypasses for all trades involving that pair. Although the current `_isTradeAndNotInSystem` logic appears robust against this specific scenario, careful management of roles is crucial to prevent future misconfigurations.

**Recommendation:** Clearly document the intended use and implications of the `INTERN_SYSTEM` role. Implement additional checks or safeguards within the `grantRole` function to prevent `mainPair` from being assigned this role if it is not intended to be fee-exempt. Regular audits of role assignments are also recommended.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5440...61b0`](https://bscscan.com/address/0x544028231562a43b106fbceca722b65cb5c861b0) |
| **Network** | BNB Chain |
| **Price** | $2.3100 |
| **24h Volume** | $716.2K |
| **Liquidity** | $10.05M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 98.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8951 buys / 8710 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is OLY a scam?

Based on automated analysis, OLY scores 68/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is OLY safe to buy?

Our scanner flagged a risk score of 68/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has OLY been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x6865704ff097b1105ed42b8517020e14fe9a2abd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/oly-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-27*
