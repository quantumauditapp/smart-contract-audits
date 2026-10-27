---
token: World Liberty Financial
ticker: WLFI
network: ethereum
risk_score: 20
status: low
date: 2026-09-12
---

# World Liberty Financial (WLFI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/world-liberty-financial-eth)

---

## Audit Summary

The WorldLibertyFinancialV3 contract, serving as an upgradeable ERC20 token with integrated vesting and registry logic, has been audited. The contract leverages OpenZeppelin's upgradeable libraries and implements a system for users to 'elect' vesting updates, which can alter their category and, in some cases, burn a portion of their token allocation. The audit identified a high-severity centralization risk due to the owner's extensive control over vesting updates and token burning, as well as medium-severity concerns regarding potential signature replay in user-initiated elections and an economic incompatibility for certain claimed users. Overall, the contract demonstrates good adherence to OpenZeppelin standards but requires careful consideration of its centralized control mechanisms and specific vesting logic implications.

> **Final Recommendation:** It is recommended to review the extent of centralized control held by the owner and authorized signer, considering if any functions could be decentralized or made more transparent. Implement a robust nonce mechanism for all signature-based operations to prevent replay attacks. Additionally, re-evaluate the economic implications for users prevented from updating their vesting due to prior claims, ensuring the design aligns with intended user experience and fairness.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract utilizes OpenZeppelin's upgradeable components, including `Ownable2StepUpgradeable`, `ERC20Upgradeable`, and `SafeERC20`, contributing to a robust technical foundation (7.2 Code… |
| **Governance / Economics** | 5/10 | Medium | The contract exhibits a high degree of centralized control, with the `owner` (a multisig) having the ability to unilaterally initiate vesting updates for any account, potentially leading to token… |
| **Upgrades** | 4/10 | Medium | The contract is deployed behind a TransparentUpgradeableProxy and uses OpenZeppelin's upgradeable base contracts, indicating a well-established upgrade pattern (7.1 Architecture, 7.7 Upgrades). The… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Signature Replay Vulnerability in `electVestingUpdate`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `electVestingUpdate` function relies on an ECDSA signature for authorization, using `account` and `deadline` as part of the signed message. However, it does not incorporate a unique `nonce` for each signature. While `_msgSender()` ensures the caller is the `account` in the signature, the absence of a nonce means that a valid signature for a future `deadline` could potentially be replayed if the transaction fails or if the user wishes to invalidate a previously signed message before the deadline. This could lead to unintended or duplicate vesting updates.

**Recommendation:** Integrate a nonce into the signed message for `electVestingUpdate`. This nonce should be managed on-chain (e.g., incremented after each successful use or tied to an EIP-712 `nonces` mapping) to ensure that each signature can only be used once, effectively preventing replay attacks.


### `M-02` — Incompatibility for Claimed Non-Retail Users  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_electVestingUpdate` function explicitly reverts if `alreadyClaimed > 0` when attempting to transition an account to `TERMINAL_NON_RETAIL_CATEGORY` (which occurs for `isKnownNonRetailCategory` users). This means users who were in categories 2-20 and have claimed any amount of their allocation are permanently blocked from electing this specific vesting update. This design choice might lead to an undesirable user experience or lock certain users into less favorable vesting terms, potentially preventing them from accessing intended benefits of the `TERMINAL_NON_RETAIL_CATEGORY`.

**Recommendation:** Review the business logic behind preventing claimed non-retail users from updating their vesting category. If this is an intentional design, ensure it is clearly communicated to users. If not, consider adjusting the logic to allow such transitions, perhaps by requiring a full burn of claimed tokens or a different mechanism to handle prior claims.


### `M-03` — Centralized Control Over Vesting Updates and Token Burning  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ownerElectVestingUpdatesFor` function allows the contract owner (a multisig) to unilaterally trigger vesting updates for any array of accounts. This process can lead to the burning of 10% of an account's allocation if the account is in a 'known non-retail category' and has not claimed any tokens. This grants significant power to the owner to alter user vesting terms and reduce token supply without direct user consent for specific updates. The `authorizedSigner` also holds substantial power via `electVestingUpdate`.

**Recommendation:** Consider implementing a more decentralized or time-locked mechanism for owner-initiated vesting updates, especially those involving token burning. For instance, a governance vote or a timelock could be introduced before such significant changes are applied. Clearly document the extent of the owner's and authorized signer's control and its implications for token holders.


### `L-01` — Dependency on `WorldLibertyFinancialV2` Storage Layout  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `WorldLibertyFinancialV3` contract inherits from `WorldLibertyFinancialV2`. In upgradeable contract systems, maintaining strict storage compatibility between inherited contracts and their upgrades is crucial to prevent storage collisions and data corruption. Without the source code for `WorldLibertyFinancialV2`, it is assumed that proper storage layout practices (e.g., using `__gap` arrays for future expansion) have been diligently followed in `V2` to ensure `V3`'s storage remains aligned.

**Recommendation:** Ensure that the `WorldLibertyFinancialV2` contract strictly adheres to OpenZeppelin's upgradeable storage layout guidelines, including the use of `__gap` arrays to reserve storage slots for future upgrades. A thorough review of `V2`'s storage layout in conjunction with `V3`'s is recommended to confirm compatibility.


### `I-01` — Lack of Event for Batch Owner Vesting Updates  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ownerElectVestingUpdatesFor` function iterates through an array of accounts, calling `_electVestingUpdate` for each. While `_electVestingUpdate` emits a `VestingUpdated` event for individual accounts, there is no overarching event emitted by `ownerElectVestingUpdatesFor` itself. This makes it harder for off-chain monitoring systems to track when a batch of owner-initiated vesting updates has occurred, or to identify the specific transaction that triggered multiple updates.

**Recommendation:** Consider emitting an event from `ownerElectVestingUpdatesFor` that includes the `owner` address and the array of `_accounts` for which updates were initiated. This would improve transparency and ease of monitoring for batch operations.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xda5e...bef6`](https://etherscan.io/address/0xda5e1988097297dcdc1f90d4dfe7909e847cbef6) |
| **Network** | Ethereum |
| **Price** | $0.05629 |
| **24h Volume** | $356.7K |
| **Liquidity** | $4.74M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 74.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 176 buys / 75 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x7f2869b24d83f03e0438c045ce24fd18045b2b6cdec47cd7b62e67e2284d1be9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/world-liberty-financial-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
