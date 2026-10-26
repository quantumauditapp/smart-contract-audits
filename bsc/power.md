---
token: Power
ticker: POWER
network: bsc
risk_score: 59
status: medium
date: 2026-09-03
---

# Power (POWER) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 59/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/power-bsc)

---

## Audit Summary

The Power Wrapped Token contract is an ERC-677 compliant token with burn and mint capabilities, built upon well-audited Chainlink and OpenZeppelin libraries. It features a two-step ownership transfer and a maximum supply cap. The primary risk identified is the centralized control over token supply through the owner's ability to manage minter and burner roles, despite the owner being a multisig. Minor issues include the use of deprecated function names and the absence of an emergency pause mechanism.

> **Final Recommendation:** To enhance the security and decentralization of the Power Wrapped Token, consider implementing a more robust governance mechanism for critical functions like minting and burning. This could involve a time-locked multisig or a community-driven governance system to reduce the reliance on a single administrative entity. Additionally, evaluate the necessity of an emergency pause feature to provide a safety net against unforeseen circumstances.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract is built upon well-audited OpenZeppelin and Chainlink libraries, providing a robust foundation for ERC-20 and ERC-677 functionalities. It includes a `validAddress` modifier to prevent… |
| **Governance / Economics** | 3/10 | High | The contract utilizes a two-step ownership transfer mechanism, enhancing security for owner changes. The owner is a multisig, mitigating single points of failure for administrative control. However… |
| **Upgrades** | 4/10 | Medium | The contract is not designed as an upgradeable proxy, meaning its logic cannot be changed post-deployment. This eliminates risks associated with upgrade mechanisms, such as proxy implementation… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control over Token Supply  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract owner has the exclusive ability to grant and revoke minter and burner roles. This means a single entity (the multisig owner) ultimately controls the token's supply dynamics. While a multisig enhances security over a single EOA, the concentrated power remains a significant centralization risk. A compromise of the multisig or malicious intent could lead to arbitrary minting or burning, impacting token value and integrity. (7.3 Access Control, 7.4 Economic)

**Recommendation:** Implement a more decentralized approach for critical functions like minting and burning, such as a time-locked governance mechanism or a multi-signature scheme with a higher threshold for these specific actions. Clearly communicate this centralization risk to users.


### `L-01` — Deprecated `increaseApproval` and `decreaseApproval` Functions  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `BurnMintERC677` contract exposes `increaseApproval` and `decreaseApproval` functions. While these functions internally call the safer `increaseAllowance` and `decreaseAllowance` from OpenZeppelin's `ERC20`, the `*Approval` naming convention is deprecated due to known front-running vulnerabilities associated with the pattern of modifying allowances directly. (7.2 Code Security)

**Recommendation:** Consider renaming these functions to `increaseAllowance` and `decreaseAllowance` to align with current best practices and avoid confusion, or remove them if their functionality is redundant with the inherited `increaseAllowance`/`decreaseAllowance`.


### `I-01` — Lack of Emergency Pause Mechanism  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `PowerWrappedToken` contract does not include a mechanism to pause token transfers or minting/burning operations in an emergency. In the event of a critical vulnerability, a market exploit, or other unforeseen circumstances, the inability to halt operations could lead to significant loss of funds or system instability. (7.8 Operations)

**Recommendation:** Evaluate the need for an emergency pause mechanism. If deemed necessary, integrate a `Pausable` contract (e.g., from OpenZeppelin) to allow the owner or a designated role to temporarily halt critical functions.


### `I-02` — High `MAX_SUPPLY` Value  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MAX_SUPPLY` for the token is set to `10^27` (1 billion tokens with 18 decimals). While this is a hard cap, it represents a very large potential supply. This is not a vulnerability in itself, but it implies that the token's value proposition might rely on controlled minting rather than scarcity, and any compromise of the minter role could lead to a massive inflation event. (7.4 Economic)

**Recommendation:** Ensure that the implications of such a high maximum supply are well-understood and communicated to token holders. Reinforce the security measures around the minter role.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9dc4...1223`](https://bscscan.com/address/0x9dc44ae5be187eca9e2a67e33f27a4c91cea1223) |
| **Network** | BNB Chain |
| **Price** | $0.08706 |
| **24h Volume** | $14.7K |
| **Liquidity** | $19.9K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 81.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 585 buys / 631 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x73ea6cc8d4dcfaf52d309800f8428d57e6dc3a2b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/power-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
