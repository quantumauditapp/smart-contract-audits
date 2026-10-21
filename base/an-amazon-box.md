---
token: An Amazon Box
ticker: BOX
network: base
risk_score: 36
status: medium
date: 2026-09-12
---

# An Amazon Box (BOX) — Smart Contract Security Analysis | Base

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/an-amazon-box-base)

---

## Audit Summary

The StonkToken contract is an ERC-20 token implementation, inheriting from OpenZeppelin's battle-tested contracts. It features a custom `tokenURI` function that retrieves metadata from an external `launcher` contract. The primary risks identified relate to the high centralization of initial token supply and the reliance on an external contract for metadata, which could impact user experience or present a vector for misleading information.

> **Final Recommendation:** It is recommended to carefully consider the implications of centralizing the entire token supply to a single `launcher` address. Implement robust security measures for this address, such as a multi-signature wallet or a time-locked vault, to mitigate the risk of compromise. Additionally, ensure the `IStonkLauncherBaseURI` contract at the `launcher` address is secure and reliable, as its integrity directly impacts the token's metadata presentation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The StonkToken contract is built upon OpenZeppelin's ERC-20 implementation, providing a solid foundation for code security (7.2) and standard compliance. The custom `_hexAddress` function is… |
| **Governance / Economics** | 2/10 | High | The economic model (7.4) of StonkToken is straightforward: a fixed total supply is minted entirely to the `launcher` address during deployment. This design choice centralizes the initial distribution… |
| **Upgrades** | 6/10 | Medium | The StonkToken contract is not designed with upgradeability in mind (7.7), as indicated by the absence of proxy patterns or upgrade-related modules. This simplifies the architecture by removing… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 2 Informational_

### `H-01` — Centralization of Initial Token Supply  *(Severity: High · Status: Unresolved)*

The `StonkToken` contract mints the entire `totalSupply_` to the `launcher_` address during construction. This design choice places all initial tokens under the control of a single address. If the `launcher` address were to be compromised, all tokens could be stolen or misused, representing a significant single point of failure for the token's initial distribution and ecosystem.

**Recommendation:** Consider distributing the initial token supply across multiple addresses, such as a multi-signature wallet, a timelock contract, or a vesting schedule, to reduce the risk associated with a single point of failure. If a single `launcher` address is necessary, ensure it is secured with the highest possible operational security measures.


### `M-01` — Reliance on External Contract for Token Metadata  *(Severity: Medium · Status: Unresolved)*

The `tokenURI()` function relies on an external call to `IStonkLauncherBaseURI(launcher).baseTokenURI()` to retrieve the base URI for token metadata. While a `try/catch` block handles reverts, a malicious or buggy `launcher` contract could return misleading or inappropriate metadata, impacting how the token is displayed in user interfaces. Additionally, a poorly implemented external contract could return an excessively long string, increasing gas costs for off-chain services attempting to retrieve the URI.

**Recommendation:** Ensure the `launcher` address points to a highly secure and trusted contract that is specifically designed to provide reliable metadata. Implement monitoring for the `launcher` contract's behavior. Consider adding a mechanism to update the `launcher` address in a controlled manner (e.g., via governance) if the current `launcher` becomes compromised or unreliable, although this would introduce upgradeability considerations.


### `I-01` — Unused `creator` Address Variable  *(Severity: Informational · Status: Unresolved)*

The `creator` address is set as an immutable variable in the constructor but is never referenced or utilized within any other function of the `StonkToken` contract. While not a vulnerability, it represents dead code or a potentially intended feature that was not fully implemented.

**Recommendation:** If the `creator` address is intended to have a role, implement the corresponding logic. Otherwise, consider removing the `creator` variable to reduce contract size and improve clarity, or document its intended off-chain purpose.


### `I-02` — Custom `_hexAddress` Function  *(Severity: Informational · Status: Unresolved)*

The contract implements a custom `_hexAddress` function to convert `address(this)` to a hexadecimal string. While functionally correct and efficient, OpenZeppelin's `Strings.toHexString` provides similar functionality and is a widely adopted, audited utility. Using standard library functions can improve code readability and maintainability.

**Recommendation:** Consider replacing the custom `_hexAddress` function with `Strings.toHexString(address(this))` from OpenZeppelin's `utils/Strings.sol` for consistency with common practices and leveraging audited library code.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4d2e...1fc2`](https://basescan.org/address/0x4d2eff441848e1c21a207ffbe90295e7db801fc2) |
| **Network** | Base |
| **Price** | $0.0003285 |
| **24h Volume** | $167.4K |
| **Liquidity** | $68.5K |
| **Volume / Liquidity** | 2.4× |
| **Token Age** | 11d |
| **Top-10 Holders** | 24.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 406 buys / 385 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x795cd8715cc2c939b1a921327f43befa5f7fc2c4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/an-amazon-box-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
