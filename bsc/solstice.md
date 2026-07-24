---
token: Solstice
ticker: SLX
network: bsc
risk_score: 78
status: critical
date: 2026-07-23
---

# Solstice (SLX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 78/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/solstice-bsc)

---

## Audit Summary

The BurnMintERC20 contract provides a standard ERC20 token with controlled minting and burning capabilities, leveraging OpenZeppelin's battle-tested libraries. The contract exhibits good code quality and includes checks against common vulnerabilities like reentrancy and integer overflows. However, the design incorporates significant centralization through the `DEFAULT_ADMIN_ROLE`, which controls token supply and administrative functions, posing a high operational risk if not managed securely. The contract is not upgradeable, ensuring immutability of its logic.

> **Final Recommendation:** It is recommended to secure the `DEFAULT_ADMIN_ROLE` with a robust multi-signature wallet to mitigate the single point of failure risk and enhance operational security. Implement a two-step transfer process for critical administrative roles, if possible, to prevent accidental loss of control. Ensure comprehensive documentation of the `s_ccipAdmin` role's external dependencies and its impact on the broader protocol to avoid misunderstandings and potential misuse.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract `BurnMintERC20` is built upon battle-tested OpenZeppelin libraries (ERC20, ERC20Burnable, AccessControl v4.8.3), enhancing its security foundation. It correctly implements custom error… |
| **Governance / Economics** | 1/10 | High | The token design exhibits a high degree of centralization, with the `DEFAULT_ADMIN_ROLE` possessing the authority to grant `MINTER_ROLE` and `BURNER_ROLE`, thereby controlling the total token supply… |
| **Upgrades** | 3/10 | High | The `BurnMintERC20` contract is not designed as an upgradeable proxy, meaning its logic cannot be modified post-deployment (7.7 Upgrades). This eliminates upgrade-related risks such as proxy storage… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control of Token Supply  *(Severity: Medium · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` has the authority to grant and revoke `MINTER_ROLE` and `BURNER_ROLE`. This means a single entity (or a small group if a multi-sig is used for the admin address) has complete control over the token's total supply through minting and burning capabilities. While this may be an intended design for a managed token, it represents a significant centralization risk (7.3 Access Control, 7.4 Economic).

**Recommendation:** If a centralized token supply is intended, ensure that the `DEFAULT_ADMIN_ROLE` is managed by a highly secure, multi-signature wallet with robust operational procedures. Clearly communicate this centralization to users and stakeholders.


### `M-02` — Single Point of Failure for DEFAULT_ADMIN_ROLE  *(Severity: Medium · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE`, initially assigned to `msg.sender` during deployment, holds extensive administrative power, including managing minter/burner roles and the `s_ccipAdmin` address. If this single administrative address is compromised, lost, or becomes inaccessible, the entire token's administrative functions could be jeopardized or rendered inoperable (7.3 Access Control, 7.8 Operations).

**Recommendation:** It is strongly recommended to assign the `DEFAULT_ADMIN_ROLE` to a robust multi-signature wallet (e.g., Gnosis Safe) rather than a single Externally Owned Account (EOA). Implement strict key management and operational security protocols for this multi-sig wallet.


### `L-01` — Lack of Two-Step Transfer for DEFAULT_ADMIN_ROLE  *(Severity: Low · Status: Unresolved)*

While `AccessControl` allows for granting and revoking roles, there isn't an explicit two-step transfer mechanism for the `DEFAULT_ADMIN_ROLE` itself. Directly granting the `DEFAULT_ADMIN_ROLE` to a new address and then revoking it from the old one in separate transactions carries a risk of accidental loss of administrative control if an incorrect address is provided or if the transaction fails midway (7.3 Access Control, 7.8 Operations).

**Recommendation:** Consider implementing a custom two-step transfer mechanism for the `DEFAULT_ADMIN_ROLE` (e.g., `proposeAdmin` and `acceptAdmin`) to prevent accidental loss of control. This adds an extra layer of security by requiring explicit acceptance from the new administrator.


### `I-01` — Unclear External Implications of s_ccipAdmin Role  *(Severity: Informational · Status: Unresolved)*

The `s_ccipAdmin` role is managed by the `DEFAULT_ADMIN_ROLE` and is intended for 'registering with the CCIP token admin registry.' However, the specific powers and implications of this role within the external CCIP protocol are not defined within this contract. This lack of clarity could lead to misunderstandings about its importance or potential misuse if the external system grants significant power to this address (7.1 Architecture, 7.6 External).

**Recommendation:** Provide comprehensive documentation detailing the purpose, responsibilities, and external dependencies of the `s_ccipAdmin` role within the broader protocol. This will help users and auditors understand its full security context and potential impact.


### `I-02` — Hardcoded Decimals  *(Severity: Informational · Status: Unresolved)*

The `i_decimals` variable is set as an immutable value during contract deployment and cannot be changed thereafter. While this is a common practice for ERC20 tokens, it means the token's decimal precision is permanently fixed and cannot be adjusted to adapt to future protocol requirements or ecosystem standards (7.1 Architecture).

**Recommendation:** No direct action is required as this is a design choice. However, ensure that the chosen decimal precision (e.g., 18 for most ERC20s) aligns with all current and anticipated future use cases for the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x02bc...c54d`](https://bscscan.com/address/0x02bcc4c181b83a8c0a342bc003389cbecb4bc54d) |
| **Network** | BNB Chain |
| **Price** | $0.1069 |
| **24h Volume** | $59.5K |
| **Liquidity** | $12.9K |
| **Volume / Liquidity** | 4.6× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 72.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 669 buys / 819 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xcd2c63e5c63d4de3313ee6759680ddb3087eac22)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/solstice-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-23*
