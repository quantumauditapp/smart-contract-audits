---
token: Sock
ticker: SOCK
network: bsc
risk_score: 31
status: low
date: 2026-09-12
---

# Sock (SOCK) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 31/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sock-bsc-16ad)

---

## Audit Summary

The SockLaunchToken contract is an ERC20 token with ERC20Permit functionality. It features a dynamic `creator()` function that determines access control for updating metadata. The primary risk identified is the reliance on external contracts for this critical access control logic, which introduces a significant external dependency.

> **Final Recommendation:** It is crucial to thoroughly audit and secure the external `ILaunchpadHook` and `ICreatorLookup` contracts, as their integrity directly impacts the security of the `SockLaunchToken`'s access control. Ensure that the `launchpad` address is controlled by a trusted entity and that the linked hook and creator lookup contracts are robust and immutable if possible. Consider implementing a fallback mechanism or a timelock for critical access control changes if the external dependencies are subject to change or potential compromise.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract implements standard ERC20 and ERC20Permit functionalities, leveraging battle-tested OpenZeppelin libraries for core token operations (7.2 Code Security). The `creator()` function… |
| **Governance / Economics** | 1/10 | High | The contract's economic model is straightforward, functioning as a standard ERC20 token with initial supply minted to the deployer (7.4 Economic). There are no complex DeFi primitives or staking… |
| **Upgrades** | 6/10 | Medium | The SockLaunchToken contract is not designed as an upgradeable proxy (7.7 Upgrades). It is deployed as a standard, immutable contract, which eliminates upgrade-related risks such as proxy storage… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 97.2% |
| **Top-3 Unlocked** | ⚠️ 98.9% |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Critical External Dependency in Creator Logic  *(Severity: High · Status: Unresolved)*

The `creator()` function, which determines the privileged address for `setMetadataURI`, relies on external contracts (`ILaunchpadHook` and `ICreatorLookup`) to dynamically resolve the creator. If these external contracts are compromised, malicious, or misconfigured, an unauthorized entity could manipulate the `creator()` return value, thereby gaining control over the `setMetadataURI` function. This introduces a significant trust assumption and a potential single point of failure on systems not directly audited.

**Recommendation:** Thoroughly audit and secure the `ILaunchpadHook` and `ICreatorLookup` contracts. Implement robust access control and immutability for these external contracts if possible. Consider adding a mechanism to update the `launchpad` address by a trusted multi-signature wallet or DAO, or a timelock for changes to the `metadataURI` if the external dependencies are deemed high risk.


### `L-01` — Unused Immutable Variable `drawer`  *(Severity: Low · Status: Unresolved)*

The `drawer` address is set as an immutable variable in the constructor but is not utilized anywhere within the `SockLaunchToken` contract's current implementation. This may indicate incomplete functionality, a placeholder for future features, or a design oversight.

**Recommendation:** If the `drawer` variable is intended for future use, document its purpose clearly. If it is no longer needed, consider removing it to reduce contract complexity and bytecode size. If it is meant to be used, ensure the functionality is implemented as intended.


### `I-01` — Centralized Control over Metadata  *(Severity: Informational · Status: Unresolved)*

The `creator()` address has the sole ability to update the `metadataURI` of the token. While this is a common pattern for token metadata management, it represents a centralized point of control for this specific aspect of the token.

**Recommendation:** Acknowledge the centralized control over metadata. If decentralization is a long-term goal, consider mechanisms for community governance or multi-signature control over metadata updates in future iterations. For now, ensure the `creator()` address is securely managed.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb3a1...a5b9`](https://bscscan.com/address/0xb3a1e1f7ae6c90c707ec3c75e99c359482fea5b9) |
| **Network** | BNB Chain |
| **Price** | $0.002045 |
| **24h Volume** | $983.2K |
| **Liquidity** | $219.9K |
| **Volume / Liquidity** | 4.5× |
| **Token Age** | 5d |
| **Top-10 Holders** | 22.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1818 buys / 1677 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x5a5a549379da0d7fe856c787dafab43c3fadc778)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sock-bsc-16ad)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
