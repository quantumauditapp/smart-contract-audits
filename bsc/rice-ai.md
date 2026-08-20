---
token: RICE AI
ticker: RICE
network: bsc
risk_score: 59
status: high
date: 2026-08-20
---

# RICE AI (RICE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 59/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/rice-ai-bsc)

---

## Audit Summary

The RiceAI contract is an ERC20 token with a time-locked transfer mechanism and a whitelist. It leverages OpenZeppelin's Ownable and ERC20 standards. The primary security concerns revolve around the high degree of centralized control held by the owner over token transfers and the complexity of the `setTransferAllowedTimestamp` function's logic. While the core ERC20 functionality is sound, the owner's ability to manipulate transfer restrictions introduces significant trust assumptions and potential for unexpected behavior.

> **Final Recommendation:** It is strongly recommended to implement a multi-signature wallet for contract ownership to mitigate the risks associated with centralized control and EOA ownership. The logic within the `setTransferAllowedTimestamp` function should be simplified and clarified with comprehensive NatSpec comments to ensure predictable behavior and ease of auditing. Clearly communicate the extent of owner control and the implications of the time-lock and whitelist mechanisms to all token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages OpenZeppelin's ERC20 and Ownable implementations, providing a solid foundation for token functionality and access control (7.2 Code Security). The `_update` override correctly… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a high degree of centralization, with the owner possessing significant control over token transfers (7.4 Economic, 7.3 Access Control). The owner can freely add or remove… |
| **Upgrades** | 6/10 | Medium | The contract is not designed with an upgrade mechanism, meaning its logic is immutable once deployed (7.7 Upgrades). This eliminates upgrade-related risks such as proxy misconfigurations or storage… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control Over Token Transfers  *(Severity: High · Status: Unresolved)*

The `Ownable` contract grants the owner extensive power to control token transfers. The owner can arbitrarily add/remove addresses from the whitelist using `addToWhitelist` and `removeFromWhitelist`, allowing them to bypass the `transferAllowedTimestamp`. More critically, the owner can manipulate the `transferAllowedTimestamp` itself via `setTransferAllowedTimestamp`, potentially extending the lock indefinitely or unlocking tokens prematurely for all non-whitelisted users. This introduces a single point of failure and significant trust assumptions, impacting 7.3 Access Control, 7.4 Economic, and 7.8 Operations.

**Recommendation:** Consider implementing a multi-signature wallet for ownership or introducing a time-lock for critical owner actions (e.g., changing `transferAllowedTimestamp` or managing the whitelist) to reduce the risk of a single point of compromise or malicious action. Clearly communicate the extent of owner control to token holders.


### `M-01` — Ambiguous and Complex `setTransferAllowedTimestamp` Logic  *(Severity: Medium · Status: Unresolved)*

The `setTransferAllowedTimestamp` function contains complex conditional logic involving `transferAllowedTimestamp` and an `ETA` variable. The initial condition `if (transferAllowedTimestamp > block.timestamp && ETA == 0)` allows the owner to set `transferAllowedTimestamp` to *any* value, effectively bypassing the `ETA` mechanism if `ETA` has not been set. This could lead to unexpected behavior, such as an indefinite extension of the lock or an immediate unlock, depending on the owner's intent. The purpose and implications of the `ETA` variable are not immediately clear and could be simplified, impacting 7.2 Code Security and 7.4 Economic.

**Recommendation:** Refactor the `setTransferAllowedTimestamp` function to simplify its logic and clearly define the rules for modifying the transfer timestamp. Ensure that the intended behavior (e.g., only allowing extensions, or only allowing reductions within certain bounds) is explicitly enforced and easily auditable. Add comprehensive NatSpec comments explaining the logic and the role of `ETA`.


### `L-01` — EOA Ownership  *(Severity: Low · Status: Unresolved)*

The contract is currently owned by an Externally Owned Account (EOA). If the private key associated with this EOA is compromised, all owner-controlled functions, including whitelisting and modifying the transfer timestamp, could be maliciously exploited. This introduces a single point of failure for critical operations, impacting 7.8 Operations and 7.3 Access Control.

**Recommendation:** Transfer ownership to a multi-signature wallet (e.g., Gnosis Safe) to enhance security and require multiple approvals for critical operations. This distributes trust and reduces the risk associated with a single compromised key.


### `I-01` — Lack of Event for `ETA` Changes  *(Severity: Informational · Status: Unresolved)*

The `ETA` variable plays a role in the `setTransferAllowedTimestamp` logic, but there is no event emitted when `ETA` is set or modified. This makes it difficult for off-chain monitoring tools or users to track changes to this critical parameter, impacting 7.2 Code Security and 7.8 Operations.

**Recommendation:** Emit an event, such as `ETAUpdated(uint256 oldETA, uint256 newETA)`, whenever the `ETA` variable is set or changed within the `setTransferAllowedTimestamp` function. This improves transparency and allows for better off-chain monitoring.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb576...98d3`](https://bscscan.com/address/0xb5761f36fdfe2892f1b54bc8ee8babb2a1b698d3) |
| **Network** | BNB Chain |
| **Price** | $0.005634 |
| **24h Volume** | $938.0K |
| **Liquidity** | $406.6K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 80.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4763 buys / 4864 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x2afdf2cd0384a3b5d7836b70c8da5e73841ba826)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/rice-ai-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-20*
