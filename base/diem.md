---
token: Diem
ticker: DIEM
network: base
risk_score: 49
status: high
date: 2026-07-26
---

# Diem (DIEM) — Smart Contract Security Analysis | Base

> **Risk Score: 49/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/diem-base)

---

## Audit Summary

The Diem contract implements an ERC20 token with staking functionalities, including a cooldown period for unstaking. The contract leverages OpenZeppelin's ERC20 and AccessControl for robust foundational security. Key risks identified include significant centralization of control under the DEFAULT_ADMIN_ROLE and a critical dependency on an external StakingV2 contract for token minting and burning, which directly impacts the token's supply and value. The staking mechanism's cooldown reset behavior also presents a medium-level risk to user experience and fund accessibility.

> **Final Recommendation:** Prioritize securing the `DEFAULT_ADMIN_ROLE` and the `MINTER_BURNER_ROLE` addresses, ideally by implementing multi-signature wallets or time-locked governance mechanisms. Conduct a thorough audit of the `StakingV2` contract, which holds the `MINTER_BURNER_ROLE`, to ensure its robustness against vulnerabilities that could impact Diem's supply. Consider implementing a maximum limit for the `cooldownDuration` to prevent potential abuse by a compromised admin. Evaluate the user experience implications of the cooldown reset mechanism and consider alternative designs or clearer warnings to users.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Diem contract demonstrates good technical practices, utilizing OpenZeppelin's battle-tested ERC20 and AccessControl libraries (7.2 Code Security). The Solidity version 0.8.26 mitigates common… |
| **Governance / Economics** | 1/10 | High | The economic model for Diem involves staking with a cooldown period, which is a standard mechanism (7.4 Economic). However, the contract exhibits high centralization, with the `DEFAULT_ADMIN_ROLE`… |
| **Upgrades** | 6/10 | Medium | The Diem contract is not designed with upgradeability in mind (7.7 Upgrades). It is deployed as a standard, non-proxy contract. This design choice means that any future modifications, bug fixes, or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 58.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control by Default Admin Role  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` in the Diem contract possesses extensive power, including the ability to set the `cooldownDuration` to any arbitrary value (potentially locking user funds indefinitely) and full management over other roles, such as the critical `MINTER_BURNER_ROLE`. This high degree of centralization means that the security of the protocol is heavily reliant on the integrity and security of the address holding the `DEFAULT_ADMIN_ROLE`. A compromise of this single address could lead to severe consequences, including fund locking or unauthorized role assignments.

**Recommendation:** Implement a multi-signature wallet for the `DEFAULT_ADMIN_ROLE` to distribute control and require multiple approvals for sensitive operations. Consider adding a time-lock mechanism for critical administrative actions, such as changing the `cooldownDuration` or granting/revoking roles, to provide a window for community review or emergency intervention.


### `H-02` — Critical Dependency on External Minter/Burner Contract  *(Severity: High · Status: Unresolved)*

The `MINTER_BURNER_ROLE` is responsible for controlling the total supply of Diem tokens through the `mint` and `burn` functions. The contract's documentation indicates that this role is intended for the `StakingV2` contract. This creates a critical external dependency: the economic stability and integrity of the Diem token are directly tied to the security and correct functioning of the `StakingV2` contract. Any vulnerability, exploit, or malicious action within `StakingV2` could lead to unauthorized minting or burning of Diem, severely impacting its value and the entire ecosystem.

**Recommendation:** Conduct a comprehensive security audit of the `StakingV2` contract to identify and mitigate any potential vulnerabilities. Ensure that `StakingV2`'s access control for minting/burning is robust and that its logic is sound. Implement monitoring for `mint` and `burn` events to detect anomalous activity quickly. Consider limiting the minting capacity or implementing a rate limit if feasible.


### `M-01` — Cooldown Period Reset on Re-initiation  *(Severity: Medium · Status: Unresolved)*

The `initiateUnstake` function resets the `coolDownEnd` timestamp for a user's entire `coolDownAmount` if they call the function again while an unstake is already pending. While the contract comment notes this behavior ('users can increase amount in cooldown, but have to wait again'), it can lead to an unexpected and potentially frustrating user experience. A user might accidentally or unknowingly reset their cooldown period, forcing them to wait longer for their entire unstaked amount, even if they only intended to add a small additional amount to the cooldown.

**Recommendation:** Consider modifying the `initiateUnstake` logic to either: 1) Prevent re-initiating an unstake if one is already pending, or 2) Allow users to add to `coolDownAmount` without resetting `coolDownEnd` if the new amount is added before the current cooldown expires. Alternatively, provide clear warnings in the UI about the cooldown reset behavior to prevent accidental delays.


### `L-01` — Lack of Maximum Cooldown Duration  *(Severity: Low · Status: Unresolved)*

The `setCooldownDuration` function, callable by the `DEFAULT_ADMIN_ROLE`, allows setting an arbitrary `uint256` value for the cooldown period. There is no upper bound or sanity check implemented for this value. While controlled by a trusted administrative role, the absence of a maximum limit could, in a worst-case scenario of a compromised admin key, lead to setting an extremely long or effectively infinite cooldown duration, thereby locking all staked user funds indefinitely.

**Recommendation:** Implement a reasonable maximum limit for the `cooldownDuration` within the `setCooldownDuration` function. This would act as a safeguard against accidental misconfiguration or malicious intent by a compromised admin, ensuring that users' funds cannot be locked for an excessively long period.


### `I-01` — Non-Upgradeable Contract Design  *(Severity: Informational · Status: Unresolved)*

The `Diem` contract is deployed as a standard, non-proxy contract and does not incorporate any upgradeability patterns (e.g., UUPS, Transparent proxies). This design choice means that any future bug fixes, feature enhancements, or protocol adjustments would necessitate deploying an entirely new contract. Migrating user funds, token balances, and staking state from the old contract to a new one can be a complex, costly, and potentially risky process, requiring significant coordination and user action.

**Recommendation:** For future iterations or new contracts, consider implementing an upgradeable proxy pattern. This would allow for seamless contract upgrades, enabling the protocol to adapt to evolving requirements, fix bugs, and introduce new features without requiring a full redeployment and migration of user assets.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf4d9...a024`](https://basescan.org/address/0xf4d97f2da56e8c3098f3a8d538db630a2606a024) |
| **Network** | Base |
| **Price** | $1,466.6400 |
| **24h Volume** | $45.7K |
| **Liquidity** | $5.78M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 91.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 332 buys / 195 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Diem a scam?

Based on automated analysis, Diem scores 68/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Diem safe to buy?

Our scanner flagged a risk score of 68/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Diem been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xbb345d35450bf9ee76f3d2ce214e8e7ac5e1071d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/diem-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-26*
