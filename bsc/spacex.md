---
token: SpaceX
ticker: SPCXB
network: bsc
risk_score: 81
status: critical
date: 2026-08-11
---

# SpaceX (SPCXB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 81/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacex-bsc)

---

## Audit Summary

The SecuritiesToken contract implements an upgradeable ERC-20 token with compliance, pausing, and a scaled UI multiplier mechanism. It leverages OpenZeppelin's upgradeable patterns and access control. The contract demonstrates good adherence to upgradeability best practices and includes robust checks for initialization and token operations. However, the system exhibits significant centralization of control in the `DEFAULT_ADMIN_ROLE` and `ISSUER_ROLE`, particularly concerning the ability to modify critical external dependencies and economic parameters. The wide range allowed for the UI multiplier also presents a notable economic risk.

> **Final Recommendation:** Strengthen the security posture by implementing multi-signature wallets for critical administrative roles, especially for the `DEFAULT_ADMIN_ROLE` which controls external contract addresses and core token parameters. Carefully review the economic implications of the wide UI multiplier range and consider implementing a more granular or time-locked mechanism for significant changes. Ensure that all external dependencies, particularly the `ComplianceClient` and `PauseManagerClient`, undergo rigorous security audits.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture (7.1) is well-structured, utilizing OpenZeppelin's upgradeable contracts and a clear separation of concerns for compliance and pausing. Code security (7.2) is generally… |
| **Governance / Economics** | 1/10 | High | Access control (7.3) is managed via `AccessControlEnumerableUpgradeable`, defining `DEFAULT_ADMIN_ROLE` and `ISSUER_ROLE`. The `DEFAULT_ADMIN_ROLE` holds significant power, including the ability to… |
| **Upgrades** | 1/10 | High | The contract is designed for upgradeability using the BeaconProxy pattern, with the provided code serving as the implementation. It correctly uses OpenZeppelin's `initializer` modifier and… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 56.9% |
| **Top-3 Unlocked** | 76.6% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control over Critical Functions and External Dependencies  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` possesses extensive control over the `SecuritiesToken` contract. This role can change the addresses of the `ComplianceClient` and `PauseManagerClient` contracts, enable/disable minting and burning, and authorize UI multiplier updates. This level of centralization means that a compromise or malicious action by a single administrator could lead to a complete system takeover, including disabling compliance, pausing all operations, or manipulating the token supply and value.

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the `DEFAULT_ADMIN_ROLE` to require multiple approvals for critical operations, such as changing external contract addresses or modifying core token parameters. Consider time-locks for highly sensitive actions to provide a window for community review or emergency intervention.


### `M-01` — Wide UI Multiplier Range with Potential Economic Impact  *(Severity: Medium · Status: Unresolved)*

The `_validateMultiplier` function allows the UI multiplier to be set within an extremely wide range, from `1e9` (0.000000001x) to `1e27` (1,000,000,000x). While controlled by privileged roles (`DEFAULT_ADMIN_ROLE` or `ISSUER_ROLE`) and limited to 365 days in the future, such drastic changes in the multiplier could significantly impact the token's perceived value and user balances, potentially leading to economic instability or unexpected behavior if not managed with extreme care.

**Recommendation:** Review the intended economic model and consider if such a wide multiplier range is truly necessary. If not, narrow the allowed range to reduce the potential for extreme value fluctuations. Implement a more robust governance process or a time-locked delay for multiplier changes, especially for significant adjustments, to allow stakeholders to react.


### `L-01` — Reliance on External Contract Security  *(Severity: Low · Status: Unresolved)*

The `SecuritiesToken` contract heavily relies on the `ComplianceClientUpgradeable` and `PauseManagerClientUpgradeable` for critical functionality, including transaction validation and pausing mechanisms. The security and correct functioning of these external contracts are paramount to the overall integrity of the token. Any vulnerabilities or malicious implementations within these external dependencies could directly compromise the `SecuritiesToken`.

**Recommendation:** Ensure that the `ComplianceClientUpgradeable` and `PauseManagerClientUpgradeable` contracts have undergone thorough security audits. Implement robust monitoring for these external contracts to detect any unexpected behavior or changes. Consider adding mechanisms to gracefully handle failures or unexpected returns from these external calls, if applicable.


### `I-01` — Significant Power of ISSUER_ROLE  *(Severity: Informational · Status: Unresolved)*

The `ISSUER_ROLE` has the authority to mint and burn tokens, as well as to authorize UI multiplier updates. This grants significant power over the token's supply and economic parameters. While this is likely an intended design, it highlights the importance of securing the keys associated with this role.

**Recommendation:** Ensure that all addresses assigned the `ISSUER_ROLE` are managed with the highest security standards, potentially using multi-signature wallets or hardware security modules. Implement strict operational procedures and access controls around these privileged accounts.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbe9d...03e1`](https://bscscan.com/address/0xbe9d156892e55e7154bcd3cb0fea677f9d3103e1) |
| **Network** | BNB Chain |
| **Price** | $136.8900 |
| **24h Volume** | $10.57M |
| **Liquidity** | $4.20M |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 91.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 18330 buys / 16629 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x977daffc095b33872e2741c19568925015c35b4d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacex-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
