---
token: Reserve Rights
ticker: RSR
network: ethereum
risk_score: 29
status: low
date: 2026-09-20
---

# Reserve Rights (RSR) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/reserve-rights-eth)

---

## Audit Summary

The RSR token contract facilitates a migration from an old RSR token, incorporating pausing, ownership, and a unique 'Enchantable' spell-casting mechanism. The audit identified critical and high-severity issues related to administrative control post-migration and potential denial-of-service vectors, alongside medium and low-severity concerns. The contract exhibits a strong move towards decentralization by renouncing ownership, but this introduces significant operational risks if not managed carefully.

> **Final Recommendation:** Prioritize addressing the critical and high-severity issues before deployment or immediately post-deployment if already live. Specifically, review the administrative control flow after ownership renouncement to ensure the pausing mechanism remains functional and recoverable. Implement safeguards for the `_oldBal` loop to prevent denial of service for users. Additionally, ensure all arithmetic operations on `uint64` variables are protected against overflow. Conduct thorough testing of the migration process and administrative role transitions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The RSR token contract (7.1 Architecture) implements a complex migration mechanism from an old token, including custom balance and allowance crossing logic. It leverages OpenZeppelin's ERC20… |
| **Governance / Economics** | 8/10 | Low | The contract's economic model centers on a fixed supply and a migration process from an old RSR token. A significant design choice is the renouncement of the `owner` role after the `moveToWorking`… |
| **Upgrades** | 7/10 | Low | The RSR contract is not designed as an upgradeable proxy (7.7 Upgrades). Its logic is immutable once deployed, which eliminates upgrade-related risks such as proxy misconfigurations or logic contract… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Potential `uint64` Overflow in `_siphon`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_siphon` function contains the operation `weights[from][newTo] += weight;`. Both `weights` and `weight` are `uint64`. While Solidity 0.8.4 automatically checks for overflows, if `weights[from][newTo]` is already close to `type(uint64).max` (approximately 1.8e19) and a non-zero `weight` is added, the transaction will revert. This could lead to a denial of service for specific `siphon` operations, preventing the intended reallocation of weights.

**Recommendation:** Add an explicit `require` check before the addition to ensure `weights[from][newTo] + weight` does not exceed `type(uint64).max`. For example: `require(weights[from][newTo] <= type(uint64).max - weight, 'RSR: weight addition overflow');`.


### `M-02` — Permanent Loss of Pausing Mechanism Control Post-Ownership Renouncement  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `moveToWorking` function calls `_transferOwnership(address(0))`, permanently renouncing the `owner` role. After this, the `castSpell` function (which sets the `_mage` role) becomes unusable. The `onlyAdminOrPauser` modifier then relies solely on the `pauser` address. If the `pauser` subsequently calls `renouncePauser()`, the `pauser` address becomes `address(0)`. At this point, no address can satisfy the `onlyAdminOrPauser` modifier, making `pause()`, `unpause()`, `changePauser()`, and `renouncePauser()` permanently inoperable. This results in a complete and irreversible loss of control over the token's pausing fun

**Recommendation:** Consider a mechanism to allow the `pauser` role to be transferred or recovered even after ownership is renounced. For example, implement a multi-signature wallet as the `pauser` or introduce a time-locked recovery mechanism. Alternatively, if the intention is to fully decentralize, explicitly state the implications of `pauser` renouncement and ensure the community understands the irreversible nature of this action.


### `M-03` — Denial of Service in `_oldBal` due to Unbounded Loop  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_oldBal` internal view function iterates through `origins[account].length()` to calculate an account's balance. The `origins` set can grow indefinitely via the `_siphon` function, which is callable by `onlyAdmin` during the `SETUP` phase. If a large number of `from` addresses siphon to a single `newTo` address, `origins[newTo]` could become very large. When `balanceOf(newTo)` is called, the `_oldBal` loop could exceed the block gas limit, causing the transaction to revert. This would effectively make the `balanceOf` function (and any other function relying on it, like `transfer`) unusable for that account, leading

**Recommendation:** Implement a pagination mechanism or a maximum limit for the `origins` set size to prevent unbounded growth. Alternatively, refactor the `_oldBal` calculation to avoid iterating over a potentially large, unbounded collection within a single transaction. Consider a 'claim' pattern where users explicitly claim their weighted balances, rather than calculating it on-the-fly for every `balanceOf` call.


### `L-01` — Allowance Migration Bypass by `approve` and `permit`  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `approve` and `permit` functions directly set `allowanceCrossed[_msgSender()][spender] = true;`. This flag is intended to ensure that the `oldRSR.allowance` is migrated only once via the `ensureAllowanceCrossed` modifier. However, by setting `allowanceCrossed` to `true` directly, `approve` and `permit` bypass the initial migration of the old allowance for that specific `(owner, spender)` pair. If a user calls `approve` or `permit` before their `oldRSR.allowance` has been migrated, their old allowance will never be considered for the new RSR token, potentially leading to a lower effective allowance than expected.

**Recommendation:** Consider modifying `approve` and `permit` to first call `ensureAllowanceCrossed(_msgSender(), spender)` before performing the new approval. This would ensure that any existing `oldRSR` allowance is migrated before being potentially overwritten by the new approval.


### `I-01` — Convoluted `_oldBal` Calculation Logic  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_oldBal` function's logic for determining an account's old balance is somewhat convoluted. It checks `if (!hasWeights[account])` to assign `oldRSR.balanceOf(account)` directly, otherwise it sums weighted balances. An account gains `hasWeights[account] = true` if it acts as a `from` address in `_siphon`. If an account has a direct `oldRSR` balance but also participates in `_siphon` as a `from` address, its direct `oldRSR` balance is only included if it siphons its own balance to itself (`_siphon(from, from, from, WEIGHT_ONE)`). While this logic appears to be functionally correct given the `_siphon` implementation,

**Recommendation:** Add detailed NatSpec comments to the `_oldBal` and `_siphon` functions explaining the exact conditions under which an account's direct `oldRSR` balance is included versus its weighted balances, and how `hasWeights` affects this calculation. This will improve code clarity and maintainability.


### `I-02` — Unused `Enchantable` Features Post-Migration  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `Enchantable` contract introduces a `_mage` role and a `castSpell` function, which allows the `owner` to temporarily grant `_mage` privileges to a `Spell` contract. However, the `castSpell` function is `onlyOwner`. After `moveToWorking` is called, the `owner` role is renounced (`_transferOwnership(address(0))`). This means `castSpell` can never be called again, rendering the entire `Enchantable` mechanism (including the ability to set a `_mage` or cast any `Spell`) permanently unusable after the token transitions to the `WORKING` phase.

**Recommendation:** If the `Enchantable` features are intended for use only during the `SETUP` phase, document this clearly. If they were intended for post-migration use, the access control for `castSpell` would need to be re-evaluated to allow a non-renounced role (e.g., `pauser` or a new dedicated role) to invoke it.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3206...5d70`](https://etherscan.io/address/0x320623b8e4ff03373931769a31fc52a4e78b5d70) |
| **Network** | Ethereum |
| **Price** | $0.001596 |
| **24h Volume** | $93.3K |
| **Liquidity** | $909.3K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 53.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 50 buys / 53 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xdb6925ea42897ca786a045b252d95aa7370f44b4-0xe72b141df173b999ae7c1adcbf60cc9833ce56a8-0x320623b8e4ff03373931769a31fc52a4e78b5d70)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/reserve-rights-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-20*
