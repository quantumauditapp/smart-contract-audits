---
token: MUSWORLD
ticker: MUSEWORLD
network: base
risk_score: 37
status: medium
date: 2026-09-21
---

# MUSWORLD (MUSEWORLD) — Smart Contract Security Analysis | Base

> **Risk Score: 37/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/musworld-base)

---

## Audit Summary

The LaunchToken contract is a standard ERC20 token with EIP-2612 permit functionality, built upon battle-tested OpenZeppelin libraries. The custom logic is minimal, primarily involving the setting of immutable addresses and initial token minting in the constructor. The contract exhibits high code quality and security due to its simplicity and reliance on audited components, resulting in a low overall risk profile.

> **Final Recommendation:** The LaunchToken contract is a well-implemented ERC20 token, benefiting significantly from its simplicity and reliance on battle-tested OpenZeppelin libraries. The primary recommendations are to review the purpose of the unused `launcher` variable and consider explicitly declaring `metadataURI` as `immutable` if its value is not intended to change post-deployment. Ensure that the centralized initial token distribution aligns with the project's decentralization goals.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1) is robust, leveraging OpenZeppelin's ERC20 and ERC20Permit implementations, which are widely audited and secure. Code security (7.2) is high due to minimal custom… |
| **Governance / Economics** | 2/10 | High | The economic model (7.4) is a standard ERC20 token, with the initial supply minted entirely to the deployer, which is a common but centralized distribution method (L-01). There are no governance… |
| **Upgrades** | 6/10 | Medium | The LaunchToken contract is not designed to be upgradeable (7.7), which eliminates all risks associated with upgrade mechanisms, such as proxy implementation bugs or administrative key compromises… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 62.4% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 1 Low · ⚪ 4 Informational_

### `L-01` — Centralized Initial Token Distribution  *(Severity: Low · Status: Unresolved)*

The constructor of the `LaunchToken` contract mints the entire initial `supply` to `msg.sender` (the `factory` address). This means that the deployer of the contract holds 100% of the initial token supply. While common for token launches, this represents a single point of control over the token's initial distribution.

**Recommendation:** Projects should clearly communicate this centralized initial distribution to their community. Consider implementing a more distributed initial allocation strategy, such as a vesting schedule, airdrop, or liquidity pool seeding, to mitigate risks associated with a single entity holding all tokens.


### `I-01` — Unused `launcher` Variable  *(Severity: Informational · Status: Unresolved)*

The `launcher` address is passed as a constructor argument and stored as an `immutable` public variable. However, this variable is never referenced or used within any of the contract's functions or logic.

**Recommendation:** Review the intended purpose of the `launcher` variable. If it serves no on-chain function, consider removing it to reduce contract size and improve clarity. If it's intended for off-chain use, document this clearly.


### `I-02` — `metadataURI` Not Explicitly Immutable  *(Severity: Informational · Status: Unresolved)*

The `metadataURI` variable is set in the constructor and is public, but it is not declared `immutable`. While there is no setter function, making it effectively immutable, explicitly declaring it `immutable` would clearly communicate its intended immutability and prevent any future confusion or accidental modification if the contract were to be extended.

**Recommendation:** If `metadataURI` is intended to be unchangeable after deployment, declare it as `immutable` in the contract definition.


### `I-03` — Sole Reliance on OpenZeppelin Libraries  *(Severity: Informational · Status: Unresolved)*

The `LaunchToken` contract heavily relies on OpenZeppelin's `ERC20` and `ERC20Permit` implementations. While these libraries are highly regarded and extensively audited, any undiscovered vulnerability in the specific versions used (`^0.8.20` and `^0.8.26` for `LaunchToken`) could potentially impact the security of this contract.

**Recommendation:** Regularly monitor OpenZeppelin's security advisories and updates for the versions of contracts used. While direct action on this contract might not be possible if it's not upgradeable, awareness is key for future deployments or related projects.


### `I-04` — No Direct Burning Mechanism for `factory` or `launcher`  *(Severity: Informational · Status: Unresolved)*

The contract includes an internal `_burn` function inherited from ERC20, but there is no public function exposed that allows the `factory` (deployer) or `launcher` to directly burn tokens from their own balance or from others (with approval). Tokens can only be 'burned' by transferring them to `address(0)` via standard ERC20 `transfer` or `transferFrom`.

**Recommendation:** If there is a design requirement for the `factory` or `launcher` to have a direct token burning capability, consider adding a specific public function for this purpose. Otherwise, ensure that the current method of sending to `address(0)` is sufficient for any intended tokenomics.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x882c...29f8`](https://basescan.org/address/0x882c8e35504d58979b1280fe76d6553f717029f8) |
| **Network** | Base |
| **Price** | $0.00063 |
| **24h Volume** | $1.21M |
| **Liquidity** | $202.7K |
| **Volume / Liquidity** | 6.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | 43.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2992 buys / 2018 sells |

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

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x050e44afe314c0298d695f7e7b6bb4769475d7541a37da644950a59413460360)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/musworld-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-21*
