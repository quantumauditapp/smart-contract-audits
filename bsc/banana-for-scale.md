---
token: Banana For Scale
ticker: BANANAS31
network: bsc
risk_score: 0
status: low
date: 2026-08-11
---

# Banana For Scale (BANANAS31) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/banana-for-scale-bsc)

---

## Audit Summary

The Token contract implements a standard ERC20 token with an Ownable pattern and a unique transfer mode mechanism. The contract initializes in a restricted transfer state, requiring owner action to enable transfers. A key design choice is the irreversible transition to a fully normal transfer mode, which prevents future re-introduction of transfer restrictions. This audit identified a High severity issue related to this irreversible mode transition, alongside other Medium and Low severity findings concerning operational aspects and design choices.

> **Final Recommendation:** Review the intended long-term governance model for token transfers, particularly the irreversible nature of setting `MODE_NORMAL`. If future flexibility to re-introduce transfer restrictions is desired, modify the `setMode` function to allow bidirectional transitions. Ensure clear communication to token holders regarding the initial restricted transfer state and the owner's role in enabling transfers. Consider the implications of `renounceOwnership` in conjunction with the `setMode` logic, as renouncing ownership would permanently lock the current transfer mode.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract leverages OpenZeppelin's `ERC20` and `Ownable` patterns, providing a solid foundation for token functionality and access control (7.1 Architecture). The use of `unchecked` blocks is… |
| **Governance / Economics** | 9/10 | Low | The token's economic model features a fixed supply after initial minting, with no further minting or burning capabilities (7.4 Economic). The initial `MODE_TRANSFER_RESTRICTED` requires the owner to… |
| **Upgrades** | 10/10 | Low | The contract is not designed with upgradeability patterns (e.g., proxies) (7.7 Upgrades). This means its logic is immutable once deployed, which simplifies the architecture by removing… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 50.4% |
| **LP Locked** | 50.4% — Dead Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Irreversible Transfer Mode Transition  *(Severity: High · Status: Unresolved)*

The `setMode` function includes a condition `if (_mode != MODE_NORMAL) { _mode = v; }`. This logic prevents the owner from changing the transfer mode back from `MODE_NORMAL` (0) to `MODE_TRANSFER_RESTRICTED` (1) or `MODE_TRANSFER_CONTROLLED` (2) once `MODE_NORMAL` has been set. This means that once transfers are fully enabled, the ability to re-introduce restrictions (e.g., for security incidents, regulatory changes, or specific operational needs) is permanently lost. This design choice significantly limits future governance flexibility and could pose a risk if the protocol ever needs to pause or control transfers again.

**Recommendation:** If the intention is to allow the owner to re-introduce transfer restrictions, remove the `if (_mode != MODE_NORMAL)` condition from the `setMode` function. This would allow the owner to freely switch between all defined modes. Alternatively, if the irreversible transition is intentional, ensure this design choice is clearly documented and understood by all stakeholders, acknowledging the permanent loss of control over transfer restrictions.


### `M-01` — Initial Restricted Transfer Mode Requires Owner Action  *(Severity: Medium · Status: Unresolved)*

The token contract is initialized with `_mode = MODE_TRANSFER_RESTRICTED` in its constructor. This means that immediately after deployment, all token transfers will revert with the message 'Token: Transfer is restricted'. The token will remain unusable for transfers until the owner explicitly calls `setMode(MODE_NORMAL)` to enable full transferability. This introduces an essential post-deployment operational step that, if missed or delayed, could lead to user confusion and hinder the token's initial utility.

**Recommendation:** Ensure that the deployment process includes a clear step for the owner to call `setMode(MODE_NORMAL)` immediately after deployment to enable token transfers. Provide clear documentation for users and operators regarding this initial restricted state and the necessary owner action. Alternatively, consider initializing the token in `MODE_NORMAL` if immediate transferability is desired, or provide a time-locked mechanism for the mode change.


### `L-01` — Fixed Supply and No Public Mint/Burn Functions  *(Severity: Low · Status: Unresolved)*

The `_mint` function is only invoked once during the contract's constructor to mint the initial `totalSupply` to the owner. There are no public or owner-controlled functions (e.g., `mint()`, `burn()`) provided in the `Token` contract to allow for additional token creation or destruction after deployment. This design results in a fixed total supply for the token, which might be an intentional design choice but limits flexibility for future tokenomics adjustments, such as inflation, deflation, or treasury management.

**Recommendation:** If a fixed supply is the intended design, no changes are necessary, but this should be explicitly documented. If future flexibility for supply management (minting/burning) is desired, consider adding owner-controlled functions to call the internal `_mint` and `_burn` methods, potentially with rate limits or other safeguards.


### `I-01` — Renouncing Ownership Permanently Locks Transfer Mode  *(Severity: Informational · Status: Unresolved)*

The contract inherits `renounceOwnership()` from `Ownable`. If the current owner calls this function, the contract's ownership will be transferred to the zero address, making the `setMode` function (which is `onlyOwner`) inaccessible. Given the irreversible nature of setting `MODE_NORMAL` (as described in H-01), renouncing ownership would permanently lock the token's transfer mode to its state at the time of renunciation. If `MODE_NORMAL` was set, it can never be restricted again; if it was `RESTRICTED` or `CONTROLLED` and `MODE_NORMAL` was never set, it could remain in that state indefinitely.

**Recommendation:** Ensure that the implications of `renounceOwnership()` are fully understood in the context of the `setMode` function's logic. If ownership is to be renounced, the owner should carefully consider the desired final transfer mode before doing so. Document this interaction clearly for future reference.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3d4f...a760`](https://bscscan.com/address/0x3d4f0513e8a29669b960f9dbca61861548a9a760) |
| **Network** | BNB Chain |
| **Price** | $0.009794 |
| **24h Volume** | $6.42M |
| **Liquidity** | $4.17M |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 29.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 14428 buys / 14217 sells |

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

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x7f51bbf34156ba802deb0e38b7671dc4fa32041d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/banana-for-scale-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
