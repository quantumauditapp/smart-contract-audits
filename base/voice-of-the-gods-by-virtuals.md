---
token: Voice of the Gods by Virtuals
ticker: ADM
network: base
risk_score: 44
status: medium
date: 2026-08-31
---

# Voice of the Gods by Virtuals (ADM) — Smart Contract Security Analysis | Base

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/voice-of-the-gods-by-virtuals-base)

---

## Audit Summary

The AgentToken contract is an upgradeable ERC20-like token designed with custom tax mechanisms, Uniswap V2 integration for liquidity, and a bot protection feature. The contract utilizes OpenZeppelin's upgradeable patterns and access control. While the architecture is generally sound, the audit identified several areas for improvement, particularly concerning the broad control granted to the factory contract, the incomplete implementation of bot protection, and potential vulnerabilities in the assumed auto-swap mechanism. These issues contribute to a Medium overall risk level.

> **Final Recommendation:** It is recommended to address the identified high and medium severity issues to enhance the contract's security posture. Specifically, review the broad permissions granted to the factory contract and consider implementing a more robust, potentially multi-sig, governance model for critical operations. The bot protection mechanism should be fully implemented within the transfer logic to ensure its effectiveness. Additionally, the auto-swap function should incorporate minimum output amount checks to mitigate sandwich attack risks. Finally, consider emitting events for all critical parameter initializations to improve transparency and off-chain monitoring.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages OpenZeppelin's `Initializable` and `Ownable2StepUpgradeable` for robust architecture (7.1) and access control (7.3). The use of `SafeERC20` enhances code security (7.2) for… |
| **Governance / Economics** | 3/10 | High | The contract's economic model (7.4) includes project buy/sell taxes and a swap threshold, configurable by the owner or factory. The `botProtectionDurationInSeconds` is a key economic parameter… |
| **Upgrades** | 1/10 | High | The contract is built as an upgradeable implementation using OpenZeppelin's `Initializable` pattern (7.7). The constructor correctly calls `_disableInitializers()`, and the `initialize` function is… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Incomplete Bot Protection Implementation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `botProtectionDurationInSeconds` variable is set during initialization, indicating an intent to implement a bot protection mechanism. However, the provided code snippet does not include the actual logic (e.g., within the `_transfer` function) that utilizes this duration to restrict transfers or other actions during the protected period. Without this implementation, the bot protection feature is ineffective.

**Recommendation:** Ensure the `_transfer` function or relevant transfer logic correctly implements the bot protection. This should involve checking `block.timestamp` against `fundedDate + botProtectionDurationInSeconds` and restricting transfers for non-whitelisted addresses (e.g., liquidity pools, owner) during this period.


### `M-02` — Potential for Sandwich Attacks on Auto-Swap (Assumed)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While the `_autoSwapInProgress` flag is a good reentrancy guard, the actual auto-swap function (which is not fully provided but implied by the tax mechanisms) might be vulnerable to sandwich attacks. If the swap logic does not specify a minimum output amount, malicious actors could front-run the auto-swap transaction by artificially increasing the price, then back-run it to profit from the price decrease caused by the large swap, extracting value from the protocol.

**Recommendation:** Implement a minimum output amount check for the auto-swap function to mitigate sandwich attacks. This minimum amount should be calculated based on the current price and a reasonable slippage tolerance to ensure the protocol receives a fair value for its swapped tokens.


### `M-03` — Centralized Control by Factory Contract  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `onlyOwnerOrFactory` modifier grants significant control to the `_factory` address, allowing it to perform critical operations such as adding/removing liquidity pools, managing valid callers, and setting project tax parameters. If the factory contract is compromised or has vulnerabilities, it could lead to a complete compromise of the `AgentToken` instances it deploys, including potential manipulation of token economics or liquidity.

**Recommendation:** Implement robust security measures for the factory contract, such as multi-signature ownership, time-locks for sensitive operations, or a more decentralized governance model. Re-evaluate if all `onlyOwnerOrFactory` functions truly require factory access post-deployment, or if some could be restricted to only the `owner` after initialization.


### `L-01` — Hardcoded Gas Limit for External Calls  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The constant `CALL_GAS_LIMIT` is hardcoded to `50000`. If this limit is used for external calls (e.g., to transfer tokens or interact with other contracts), it could potentially lead to a denial-of-service (DoS) if the called contract's function requires more gas than this limit. This would cause the transaction to revert, preventing the intended operation.

**Recommendation:** Re-evaluate the necessity of a hardcoded gas limit for external calls. If it is used, ensure it is sufficiently high to accommodate all legitimate operations of the called contracts. Alternatively, consider removing it if not strictly necessary, allowing the EVM to handle gas forwarding more flexibly.


### `I-01` — Lack of Event Emission for Critical Parameter Initializations  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While some parameter updates emit events, several critical parameters set during the `initialize` function (e.g., `botProtectionDurationInSeconds`, `pairToken`, `vault`, `_name`, `_symbol`, `projectBuyTaxBasisPoints`, `projectSellTaxBasisPoints`) do not have corresponding events emitted. This makes it harder for off-chain systems, such as block explorers or monitoring tools, to track the initial configuration and state of the contract.

**Recommendation:** Emit events for all critical parameters set during initialization. This improves transparency, auditability, and allows for easier monitoring and integration with off-chain services.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x55ff...2f16`](https://basescan.org/address/0x55ff51da774b8ce0ed1abaed1cb76236bc6b2f16) |
| **Network** | Base |
| **Price** | $0.001203 |
| **24h Volume** | $33.8K |
| **Liquidity** | $216.1K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 34.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 602 buys / 411 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x039f7c7e22c1c3bba5e871029ca72d5ddead295b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/voice-of-the-gods-by-virtuals-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
