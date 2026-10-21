---
token: ChipWorks
ticker: CHIP
network: base
risk_score: 51
status: medium
date: 2026-09-12
---

# ChipWorks (CHIP) — Smart Contract Security Analysis | Base

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/chipworks-base)

---

## Audit Summary

The DopplerERC20V1 contract implements an upgradeable ERC20 token with vesting schedules and a balance limit mechanism. The audit identified a High-severity issue related to centralized control of the `controller` role, which can disable critical economic parameters. Medium-severity findings include a highly restrictive pool locking mechanism and automatic exclusion of vesting beneficiaries from balance limits, potentially impacting operational flexibility and distribution control. Several Low and Informational findings were also noted, primarily concerning operational resilience and initial token distribution design.

> **Final Recommendation:** Prioritize addressing the centralized control of the `controller` role by considering a multisig or time-lock for critical functions like disabling the balance limit. Re-evaluate the `pool` locking mechanism to ensure it aligns with the intended operational use case, potentially relaxing restrictions or clarifying its purpose. Review the automatic exclusion of vesting beneficiaries from the balance limit to confirm it meets the desired economic distribution strategy. Implement an emergency pause mechanism to mitigate risks from unforeseen vulnerabilities or market events, and ensure the `controller` address is correctly set during initialization to avoid locking critical functionality.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract is built on Solady libraries, demonstrating good code quality and gas efficiency. It implements standard ERC20 and ERC20Votes functionalities, along with a custom vesting system and a… |
| **Governance / Economics** | 3/10 | High | The contract incorporates vesting schedules and a balance limit to manage token distribution (7.4 Economic). The `initialize` function includes checks for vesting schedule validity and pre-mint… |
| **Upgrades** | 7/10 | Low | The contract is designed as an upgradeable proxy using the `Initializable` pattern (7.7 Upgrades), correctly disabling initializers in the constructor and using the `initializer` modifier. This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control of `controller` Role  *(Severity: High · Status: Unresolved)*

The `controller` role, a single address, has the sole authority to call `disableBalanceLimit()`, which can permanently deactivate the `isBalanceLimitActive` flag. This flag is a critical economic parameter designed to control token distribution. While the `owner` role is managed by an OZ ProxyAdmin (implying a multisig), the `controller` is a single point of failure. If the `controller` key is compromised, an attacker could disable the balance limit, potentially leading to unintended token accumulation by malicious actors.

**Recommendation:** Consider implementing a multisig or a time-lock mechanism for the `disableBalanceLimit()` function, similar to the owner's upgrade capabilities. Alternatively, if the `controller` is intended to be a single entity, ensure robust key management practices are in place. Clearly document the responsibilities and security implications of the `controller` role.


### `M-01` — Restrictive `pool` Locking Mechanism  *(Severity: Medium · Status: Unresolved)*

The `lockPool` function, when activated by the owner, sets `isPoolLocked` to true and designates a `pool` address. Subsequently, the `_beforeTokenTransfer` hook restricts all transfers *from* this `pool` address to *only* the `DopplerERC20V1` contract itself. This highly restrictive condition could cripple the functionality of an external `pool` (e.g., an AMM, liquidity pool, or staking contract) if it is intended to distribute tokens to users, leading to operational issues or denial of service for that component of the ecosystem.

**Recommendation:** Re-evaluate the intended purpose and operational flow of the `pool` locking mechanism. If the `pool` is meant to distribute tokens, consider relaxing the transfer restrictions when locked, or provide a clear mechanism for the `pool` to operate under specific conditions. Document the exact scenarios where `pool` locking is intended and its implications for integrated protocols.


### `M-02` — Automatic Balance Limit Exclusion for Vesting Beneficiaries  *(Severity: Medium · Status: Unresolved)*

In the `initialize` function, all addresses designated as `beneficiaries` for vesting schedules are automatically added to the `isExcludedFromBalanceLimit` mapping. This means these beneficiaries are not subject to the `maxBalanceLimit` check. While this might be an intentional design choice to ensure vested tokens can be received, it reduces the effectiveness of the balance limit for a potentially large group of token holders, potentially undermining the overall purpose of controlling token distribution.

**Recommendation:** Confirm if the automatic exclusion of all vesting beneficiaries from the balance limit is the desired economic strategy. If not, consider implementing a more granular control mechanism, such as allowing the owner or controller to explicitly include/exclude beneficiaries from the balance limit after initialization, or applying the balance limit to beneficiaries after their vesting period concludes.


### `L-01` — Lack of Emergency Pause/Withdrawal Mechanism  *(Severity: Low · Status: Unresolved)*

The contract lacks a mechanism to pause token transfers or to withdraw tokens held by the contract (e.g., `vestedTokens` minted to `address(this)`) in an emergency. In the event of a critical vulnerability, a market exploit, or a severe bug in the vesting logic, the owner or controller would have no immediate way to halt operations or recover funds, potentially leading to unrecoverable losses or continued exploitation.

**Recommendation:** Consider implementing an emergency pause mechanism (e.g., using OpenZeppelin's `Pausable` contract) that allows the owner to temporarily halt token transfers. Additionally, evaluate if a controlled emergency withdrawal function for tokens held by the contract is necessary, perhaps with a time-lock or multisig requirement, to safeguard funds in extreme scenarios.


### `L-02` — Controller Address Can Be `address(0)`  *(Severity: Low · Status: Unresolved)*

The `controller` address is set during the `initialize` function. There is no explicit check to prevent `controller_` from being set to `address(0)`. If `controller_` is initialized as `address(0)`, the `disableBalanceLimit` function, which uses the `onlyController` modifier, would become permanently inaccessible, as `msg.sender` can never be `address(0)`. This would lead to an unchangeable state for the balance limit, potentially locking it active indefinitely.

**Recommendation:** Add a `require(controller_ != address(0), InvalidControllerAddress())` check within the `initialize` function to ensure the `controller` role is always assigned to a valid address. This prevents accidental misconfiguration that could render critical functionality unusable.


### `I-01` — High `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD` Values  *(Severity: Informational · Status: Unresolved)*

Both `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD` constants are set to `0.8 ether`. When used in calculations like `initialSupply * MAX_PRE_MINT_PER_ADDRESS_WAD / WAD`, this effectively allows up to 80% of the `initialSupply` to be pre-minted per address and in total during initialization. This design choice permits a highly concentrated initial distribution of tokens, which might have significant economic implications for decentralization, market liquidity, and price stability.

**Recommendation:** Review and confirm that the high pre-mint limits (80% of initial supply) align with the project's intended token distribution strategy and decentralization goals. Document the rationale behind these limits and their potential impact on the token's economic model.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x75af...1ba3`](https://basescan.org/address/0x75af968d2e58749fda1b42c58186b76f5e511ba3) |
| **Network** | Base |
| **Price** | $0.00000333 |
| **24h Volume** | $301.7K |
| **Liquidity** | $129.4K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 3d |
| **Top-10 Holders** | 43.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1450 buys / 2236 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xbcdd8383e38069f626846b94e93ee4d2c00cadfcce4b9457b0b8b04289030345)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/chipworks-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
