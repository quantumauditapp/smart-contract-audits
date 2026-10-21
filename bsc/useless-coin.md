---
token: USELESS COIN
ticker: USELESS
network: bsc
risk_score: 49
status: medium
date: 2026-09-04
---

# USELESS COIN (USELESS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/useless-coin-bsc)

---

## Audit Summary

The BurnMintERC20 token contract implements a standard ERC20 token with additional minting and burning capabilities, leveraging OpenZeppelin's AccessControl for role management. Key strengths include the use of battle-tested libraries, an immutable maximum supply, and explicit checks to prevent self-transfers. However, the contract exhibits a high degree of centralization, particularly concerning the `DEFAULT_ADMIN_ROLE`'s power to manage minter and burner roles, which directly impacts token supply. The purpose and security implications of the `s_ccipAdmin` role, an external dependency, are also not fully defined within this contract.

> **Final Recommendation:** To mitigate the identified risks, it is strongly recommended to implement a robust governance mechanism for the `DEFAULT_ADMIN_ROLE`. This should ideally involve transferring the role to a multi-signature wallet or a time-locked governance contract immediately after deployment. Additionally, thoroughly document and secure the external systems interacting with the `s_ccipAdmin` role, ensuring its intended function aligns with the overall security posture of the protocol.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract leverages battle-tested OpenZeppelin libraries for ERC20, burning, and access control, enhancing code security (7.2). It implements robust checks to prevent tokens from being sent to or… |
| **Governance / Economics** | 5/10 | Medium | The token's economic model benefits from an immutable `maxSupply` (7.4), preventing uncontrolled inflation beyond a set limit. However, the `DEFAULT_ADMIN_ROLE` holds significant power, including the… |
| **Upgrades** | 6/10 | Medium | The contract is not designed to be upgradeable (7.7), which eliminates risks associated with proxy patterns and upgradeability mechanisms. This simplifies the architecture and reduces the attack… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.7% |
| **Top-3 Unlocked** | ⚠️ 99.3% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control of Token Supply (Mint/Burn Roles)  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` has the sole authority to grant `MINTER_ROLE` and `BURNER_ROLE`. Holders of these roles can mint new tokens (up to `i_maxSupply`) or burn existing tokens. If the `DEFAULT_ADMIN_ROLE` is compromised or misused, it could lead to arbitrary manipulation of the token supply, directly impacting the token's value and the economic stability of the protocol (7.3, 7.4, 7.5).

**Recommendation:** Implement a robust, decentralized, or multi-signature governance mechanism for the `DEFAULT_ADMIN_ROLE`. Consider a timelock for critical operations like granting `MINTER_ROLE` or `BURNER_ROLE` to provide a window for community review and intervention. Ensure that the addresses holding `MINTER_ROLE` and `BURNER_ROLE` are also secured by strong access control policies.


### `M-01` — Undefined External Dependency for `s_ccipAdmin` Role  *(Severity: Medium · Status: Unresolved)*

The contract defines an `s_ccipAdmin` state variable and an interface `IGetCCIPAdmin` to expose it, with the `DEFAULT_ADMIN_ROLE` able to set this address. However, the specific functionality and security implications of this `s_ccipAdmin` role are not defined within this contract and depend entirely on external CCIP systems (7.6). Misconfiguration or vulnerabilities in these external systems could indirectly affect the protocol's security or operations.

**Recommendation:** Provide comprehensive documentation detailing the intended use, responsibilities, and security model of the `s_ccipAdmin` role and its interaction with external CCIP systems. Conduct a thorough security review of any external contracts or protocols that rely on this `getCCIPAdmin` function to understand the full attack surface.


### `L-01` — Initial Centralization of `DEFAULT_ADMIN_ROLE`  *(Severity: Low · Status: Unresolved)*

The constructor assigns the `DEFAULT_ADMIN_ROLE` to `msg.sender` (the deployer). While common, this means that immediately after deployment, a single external owned account (EOA) holds complete administrative control over the contract (7.3, 7.8). If this EOA's private key is compromised before the role is transferred, the entire access control system could be subverted.

**Recommendation:** It is a best practice to transfer the `DEFAULT_ADMIN_ROLE` to a secure, multi-signature wallet or a robust governance contract immediately after deployment. This reduces the single point of failure risk associated with a single EOA.


### `I-01` — Prevention of Self-Transfers/Approvals  *(Severity: Informational · Status: Resolved)*

The `_transfer` and `_approve` functions explicitly revert if the recipient or spender is `address(this)`. This is a good security practice (7.2) that prevents tokens from being accidentally or maliciously sent to or approved by the contract itself, which could lead to tokens becoming unrecoverable or misused within the contract's balance.

**Recommendation:** No action required. This is a positive security measure.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xba38...6d2b`](https://bscscan.com/address/0xba38b3c706f7a515ff7c8db04daa0a134ec46d2b) |
| **Network** | BNB Chain |
| **Price** | $0.2599 |
| **24h Volume** | $1.05M |
| **Liquidity** | $706.0K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 88.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3380 buys / 2676 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x1b87567de134dbe30e29953c477f1cbc3d626b6b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/useless-coin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-04*
