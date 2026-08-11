---
token: Broccoli
ticker: BROCCOLI
network: bsc
risk_score: 10
status: low
date: 2026-08-11
---

# Broccoli (BROCCOLI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/broccoli-bsc)

---

## Audit Summary

The audit of the Token contract revealed a significant design flaw in the transfer mode management, leading to an irreversible state where transfer restrictions cannot be re-enabled once set to 'normal'. This poses a high economic and operational risk. Other findings include centralized control over transfers and minor theoretical overflow concerns. The contract generally follows OpenZeppelin patterns for ERC20 and Ownable functionality.

> **Final Recommendation:** It is strongly recommended to address the critical flaw in the `setMode` function to allow the owner to re-enable transfer restrictions after setting the mode to 'normal'. This can be achieved by removing the `if (_mode != MODE_NORMAL)` condition. Additionally, consider implementing a timelock for sensitive owner actions to mitigate risks associated with centralized control. Ensure clear communication to users regarding the initial transfer restrictions and the owner's capabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract implements a standard ERC20 token with custom transfer restriction logic (7.1 Architecture). Code security (7.2 Code Security) is generally robust, leveraging OpenZeppelin's `unchecked`… |
| **Governance / Economics** | 8/10 | Low | The token's economic model (7.4 Economic) is heavily influenced by the owner's ability to control transferability. The initial state restricts all transfers, requiring owner intervention. The primary… |
| **Upgrades** | 10/10 | Low | The contract is not designed with an upgradeability pattern (7.7 Upgrades). Therefore, there are no specific upgrade-related risks to assess. Any changes to the contract's logic would require a new… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 77.8% — GoPlus SafeToken Locker |
| **Top-1 Unlocked Holder** | 20.1% |
| **Top-3 Unlocked** | 22.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Irreversible Transfer Mode Change  *(Severity: High · Status: Unresolved)*

The `setMode` function contains a condition `if (_mode != MODE_NORMAL) { _mode = v; }`. This logic prevents the owner from changing the `_mode` if it is currently `MODE_NORMAL`. Consequently, once the token's transfer mode is set to `MODE_NORMAL`, the owner permanently loses the ability to re-enable transfer restrictions (e.g., `MODE_TRANSFER_RESTRICTED` or `MODE_TRANSFER_CONTROLLED`). This removes a critical control mechanism that could be necessary for security incidents or market stability.

**Recommendation:** Remove the conditional check `if (_mode != MODE_NORMAL)` from the `setMode` function. This will allow the owner to freely switch between all defined modes, including re-enabling restrictions after the token has been in `MODE_NORMAL`. Ensure that the owner's private key is secured.


### `M-01` — Centralized Control over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The `Token` contract grants the `owner()` (deployer) significant control over token transferability through the `setMode` function. The owner can restrict all transfers (`MODE_TRANSFER_RESTRICTED`) or limit them to only transfers involving the owner (`MODE_TRANSFER_CONTROLLED`). While this offers flexibility, it introduces a high degree of centralization, where a single entity can unilaterally halt or control token movements, posing a risk of censorship or manipulation.

**Recommendation:** Consider implementing a multi-signature wallet for the `owner` address to reduce the single point of failure. For long-term decentralization, explore integrating a governance mechanism (e.g., DAO) to manage the `_mode` parameter, or transition to a fully permissionless state where `_mode` is permanently `MODE_NORMAL` after a certain period or condition.


### `L-01` — Theoretical Overflow in `unchecked` Blocks  *(Severity: Low · Status: Unresolved)*

The contract uses `unchecked` blocks for `_balances[to] += amount` in `_transfer` and `_mint`, and `_totalSupply += amount` in `_mint`. While Solidity 0.8+ defaults to checked arithmetic, `unchecked` explicitly allows overflow. Although `uint256` is extremely large, a theoretical overflow could occur if the sum of `_balances[to]` and `amount` (or `_totalSupply` and `amount`) exceeds `type(uint256).max`. This is highly improbable in practical scenarios for typical token values but is a theoretical edge case.

**Recommendation:** For maximum robustness, consider adding explicit overflow checks within the `unchecked` blocks for additions, or ensure that the design inherently prevents such large sums. However, given the practical unlikelihood for `uint256`, this is a minor concern.


### `I-01` — Initial Transfer Restriction  *(Severity: Informational · Status: Unresolved)*

The `Token` contract's constructor initializes `_mode` to `MODE_TRANSFER_RESTRICTED`. This means that immediately after deployment, no token transfers are possible until the `owner()` explicitly calls `setMode` to change it to `MODE_NORMAL` or `MODE_TRANSFER_CONTROLLED`. This is an intended design choice but is crucial for users to understand.

**Recommendation:** Ensure that this initial state and the requirement for owner action to enable transfers are clearly documented and communicated to all prospective users and participants in the token ecosystem.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x12b4...2f3b`](https://bscscan.com/address/0x12b4356c65340fb02cdff01293f95febb1512f3b) |
| **Network** | BNB Chain |
| **Price** | $0.006755 |
| **24h Volume** | $45.8K |
| **Liquidity** | $930.7K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 74.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 187 buys / 164 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xdb25c09d96c165b62f6e6f9d9b17174738d897ba)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/broccoli-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
