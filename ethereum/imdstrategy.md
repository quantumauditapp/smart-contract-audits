---
token: IMDStrategy
ticker: IMDSTR
network: ethereum
risk_score: 71
status: high
date: 2026-09-26
---

# IMDStrategy (IMDSTR) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 71/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/imdstrategy-eth)

---

## Audit Summary

The ImmutableNFTStrategy contract serves as an implementation for a UUPS proxy, designed to explicitly disable further upgrades. While the provided code for ImmutableNFTStrategy is minimal and secure in its stated purpose, a comprehensive audit of the underlying NFTStrategy contract, from which it inherits core logic, was not possible due to missing source code. This significantly limits the scope of the audit and introduces unverified risks related to the strategy's economic mechanisms, access control, and interactions with external protocols.

> **Final Recommendation:** To ensure the overall security and integrity of the protocol, it is crucial to provide the complete source code for the `NFTStrategy` base contract. A thorough audit of this core logic is necessary to identify and mitigate potential vulnerabilities related to access control, economic mechanisms, and interactions with external protocols. Additionally, a detailed review of all external dependencies, including Uniswap V4 and CryptoPunks, should be conducted to understand their implications on the strategy's security and functionality.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The `ImmutableNFTStrategy` contract is minimal, primarily overriding the `upgradeToAndCall` function to prevent further upgrades, thereby ensuring the immutability of the current implementation (7.7… |
| **Governance / Economics** | 1/10 | High | The system, as indicated by various interfaces (e.g., `IPunkStrategy`, `IPunkStrategyHook`), involves complex economic interactions such as NFT trading, fee collection, reward distribution, and… |
| **Upgrades** | 1/10 | High | The `ImmutableNFTStrategy` contract explicitly disables upgrades by reverting `upgradeToAndCall` with an `UpgradesDisabled()` error. This design choice makes the deployed proxy effectively immutable… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 2 Informational_

### `H-01` — Incomplete Audit Scope - Missing Base Contract Source  *(Severity: High · Status: Unresolved)*

The `NFTStrategy` contract, from which `ImmutableNFTStrategy` inherits its core functionality, was not provided for review. This prevents a comprehensive security assessment of the strategy's primary logic, including critical areas such as reentrancy protection, integer arithmetic, handling of funds, and complex state transitions. Without the full source, potential vulnerabilities in the base contract cannot be identified or mitigated (7.1 Architecture, 7.2 Code Security).

**Recommendation:** Provide the complete and verified source code for the `NFTStrategy` contract to enable a full and thorough security audit of the entire system. This is essential for ensuring the robustness and security of the protocol.


### `M-01` — Unaudited Access Control Mechanisms  *(Severity: Medium · Status: Unresolved)*

The interfaces (`IPunkStrategy`, `IStrategy`, `IBaseStrategyFactory`) indicate the presence of an `owner` role and various functions that modify critical parameters (e.g., `setReward`, `setPriceMultiplier`, `updateFeeBips`, `transferOwnership`). Without the source code for `NFTStrategy`, the implementation details of these access control mechanisms (e.g., whether `Ownable` is used, if there are multi-sig requirements, or if there are any re-entrancy guards on sensitive functions) cannot be verified. Improper access control could lead to unauthorized parameter changes or fund manipulation (7.3 Access Control).

**Recommendation:** Provide the source code for `NFTStrategy` to allow for a detailed review of all access control implementations. Ensure that critical functions are adequately protected, and consider implementing multi-signature wallets for sensitive administrative actions.


### `I-01` — Reliance on External Protocols  *(Severity: Informational · Status: Unresolved)*

The contract interfaces indicate significant interaction with external protocols such as Uniswap V4, CryptoPunks (`IPunks`), and a Universal Router (`IUniversalRouter`). The security and correct functioning of this strategy heavily depend on the integrity, expected behavior, and upgradeability of these external contracts. Any vulnerabilities, unexpected changes, or economic exploits in these external dependencies could directly impact the strategy (7.6 External).

**Recommendation:** Conduct a thorough review of all external dependencies, including their security audits, upgrade mechanisms, and potential failure modes. Implement robust error handling and sanity checks when interacting with external contracts to mitigate risks from unexpected behavior.


### `I-02` — Explicit Immutability via `UpgradesDisabled`  *(Severity: Informational · Status: Resolved)*

The `ImmutableNFTStrategy` contract explicitly prevents future upgrades by overriding the `upgradeToAndCall` function to unconditionally revert with `UpgradesDisabled()`. This design choice ensures that the current logic of the strategy, once deployed as a UUPS proxy implementation, cannot be altered via the standard UUPS upgrade mechanism, providing a strong guarantee of immutability for the current implementation (7.7 Upgrades).

**Recommendation:** This is a positive security feature. Ensure that this immutability aligns with the long-term operational and governance strategy for the protocol. If any future changes are anticipated, they would require a new deployment rather than an upgrade.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8027...aca2`](https://etherscan.io/address/0x80271ce20184e38f4afe90d4ca134304d197aca2) |
| **Network** | Ethereum |
| **Price** | $0.0006472 |
| **24h Volume** | $1.89M |
| **Liquidity** | $350.5K |
| **Volume / Liquidity** | 5.4× |
| **Token Age** | 11h |
| **Top-10 Holders** | 55.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1533 buys / 2020 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x070ea56ac2effba97d3c106602cf0dcdbaac6ad9acccc1ee4bdaa9f59c5af402)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/imdstrategy-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-26*
