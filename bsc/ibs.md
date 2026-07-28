---
token: IBS
ticker: IBS
network: bsc
risk_score: 22
status: medium
date: 2026-07-25
---

# IBS (IBS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 22/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ibs-bsc)

---

## Audit Summary

The audit of the Token contract reveals a critical risk profile primarily due to the implications of renounced ownership. While the contract utilizes robust OpenZeppelin libraries for ERC20, access control, and ownership management, the reported renounced ownership renders all owner-controlled functions immutable. This leads to permanent rigidity in critical parameters like tax rates and treasury addresses, and makes the initial unlimited minting power unrevocable. Several high-severity issues related to permanent minting and potential misconfiguration are identified, alongside a medium-severity issue regarding an unclear tax function and an informational finding on whitelist logic. The project's security relies heavily on the correctness of its initial deployment parameters.

> **Final Recommendation:** Given the reported renounced ownership, it is crucial to ensure that all initial deployment parameters, including tax rates, treasury addresses, and minter roles, are meticulously verified and align perfectly with the project's long-term vision. Any misconfiguration will be permanent and unchangeable. For future projects, consider whether complete ownership renouncement is truly necessary, or if a multi-signature wallet or a time-locked governance mechanism would provide a better balance between decentralization and operational flexibility. Thoroughly document the intended behavior and implications of all roles and parameters, especially the `transferTax` function, to prevent misunderstandings or misuse.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Token contract is built upon well-audited OpenZeppelin libraries (ERC20Burnable, ERC20Permit, AccessControl, Ownable2Step), which contributes to a solid foundation (7.2 Code Security). The tax… |
| **Governance / Economics** | 6/10 | Medium | The contract's economic model relies on configurable buy and sell tax rates, directed to a treasury address (7.4 Economic). The `onlyOwner` modifier initially centralizes control over these… |
| **Upgrades** | 9/10 | Low | The Token contract is not designed as an upgradeable proxy. Therefore, there are no upgrade-specific risks or considerations for this contract. Any changes to the contract's logic would require a new… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · ⚪ 1 Informational_

### `C-01` — Immutability of Critical Parameters after Ownership Renouncement  *(Severity: Critical · Status: Unresolved)*

The contract utilizes `Ownable2Step` and has numerous critical functions protected by the `onlyOwner` modifier (e.g., `setBuyRates`, `setTreasuryAddress`, `setLongGovernanceList`). If ownership is renounced, as indicated by the provided metadata, all these functions become permanently unusable. This means that critical parameters like tax rates (`longGovernanceRatio`, `shortGovernanceRatio`), treasury addresses (`treasury`, `taxTreasury`), and the various governance/whitelist mappings become immutable after deployment. While this prevents a malicious owner from changing parameters, it introduces a severe risk of rigidity, preventing any future adjustments, bug fixes, or adaptation to changi…

**Recommendation:** If immutability is the desired state, ensure all initial parameters are thoroughly audited, tested, and confirmed to be correct before deployment and renouncement. If flexibility is needed, ownership should not be renounced, or a more decentralized governance mechanism (e.g., a DAO with a timelock) should be implemented to manage these parameters. Clearly document the implications of renounced ownership for all stakeholders.


### `H-01` — Permanent Unlimited Minting Power  *(Severity: High · Status: Unresolved)*

The `MINTER_ROLE` is granted to two external addresses (`rbs` and `minter_`) in the constructor. The `mint` function, callable by anyone with `MINTER_ROLE`, allows for the creation of an arbitrary amount of new tokens. If ownership is renounced, the `grantTaxer` and `revokeTaxer` functions (which manage roles) become unusable. This means the initial `MINTER_ROLE` holders retain permanent, unlimited power to mint tokens, and this power cannot be revoked. This poses a significant risk of token inflation, value dilution, and potential for malicious actors to exploit this capability.

**Recommendation:** Implement a mechanism to revoke or limit minting power, even after ownership renouncement, if such flexibility is desired. Consider using a multi-signature wallet for the `MINTER_ROLE` to require multiple approvals for minting operations. If minting is intended to be limited, enforce a maximum total supply or a defined minting schedule within the contract logic.


### `H-02` — Permanent Zero Treasury if Misconfigured  *(Severity: High · Status: Unresolved)*

The `treasury` address, which is the recipient of collected taxes from `_collectGovernance`, is set only during the constructor via the `treasury_` argument. If ownership is renounced, the `setTreasuryAddress` function becomes unusable. This means if `treasury_` was initialized to `address(0)` during deployment, or to an incorrect/uncontrolled address, no taxes will ever be collected by the `_collectGovernance` function, leading to a permanent loss of intended revenue or funds being sent to an inaccessible address. This represents a critical operational flaw if not configured correctly at deployment.

**Recommendation:** Ensure the `treasury` address is correctly set to a secure and controlled address during deployment. If `address(0)` is intended to disable taxes, this behavior should be explicitly documented and understood by all stakeholders. Consider adding a non-zero address check in the constructor for the `treasury_` parameter if `address(0)` is never a valid target.


### `M-01` — Unclear Purpose of `transferTax` Function  *(Severity: Medium · Status: Unresolved)*

The `transferTax` function, callable by `TAXER_ROLE` holders, allows an account to transfer a percentage of a specified `amount` from `_msgSender()` to `taxTreasury`, based on the `shortGovernanceRatio`. This mechanism is unusual as it is not a tax applied automatically during token transfers, but rather a separate, explicit function call initiated by a `TAXER_ROLE` holder. The intended use case, benefit, and potential for misuse of this function are not clearly defined within the code or comments, which could lead to confusion or unintended operational scenarios.

**Recommendation:** Clarify the intended purpose and specific use cases for the `transferTax` function. Document its behavior thoroughly, including who is expected to call it, under what circumstances, and what problem it solves. Consider if this functionality is truly necessary or if it introduces unnecessary complexity or potential for misuse.


### `I-01` — Broad Whitelist Exemption Logic  *(Severity: Informational · Status: Unresolved)*

The `_collectGovernance` function's whitelist logic for tax exemption is defined as `!whitelist[from] && !whitelist[to]`. This condition means that if *either* the `from` address or the `to` address is present in the `whitelist` mapping, the transaction will be exempt from both `longGovernanceRatio` (buy tax) and `shortGovernanceRatio` (sell tax). This broad exemption might not align with all potential use cases or expectations, as a single whitelisted participant can effectively bypass taxes for a transaction involving a non-whitelisted party.

**Recommendation:** Review the whitelist logic to ensure it precisely matches the intended tax exemption policy. If a stricter exemption is desired (e.g., both `from` and `to` must be whitelisted for exemption, or only the `from` address determines the tax), adjust the condition accordingly. Document the exact behavior of the whitelist for clarity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x255e...a7cd`](https://bscscan.com/address/0x255e746abb8d9acac00d6d023e5e63e3b8dfa7cd) |
| **Network** | BNB Chain |
| **Price** | $24.9200 |
| **24h Volume** | $1.45M |
| **Liquidity** | $21.46M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 96.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5618 buys / 5173 sells |

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

## Frequently Asked Questions

### Is IBS a scam?

Based on automated analysis, IBS scores 61/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is IBS safe to buy?

Our scanner flagged a risk score of 61/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has IBS been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x2a4b99a9c4544d35e8d266111c50b67fea01d53d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ibs-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-25*
