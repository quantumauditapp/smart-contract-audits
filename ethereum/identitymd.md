---
token: Identity.md
ticker: IMD
network: ethereum
risk_score: 62
status: high
date: 2026-08-11
---

# Identity.md (IMD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 62/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/identitymd-eth)

---

## Audit Summary

The BridgedFP contract is an Omnichain Fungible Token (OFT) implementation utilizing LayerZero and OpenZeppelin's Ownable. It allows the owner to update the token's name and symbol. The contract's custom logic is minimal and appears robust, but the centralized control over metadata introduces a medium-level risk. No critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** It is recommended to implement robust security measures for the owner's private key, such as multi-signature wallets or hardware security modules, to mitigate the risk associated with centralized control over token metadata. Additionally, consider transparent communication with the community regarding any planned changes to the token's name or symbol to maintain trust and prevent confusion. Regular security reviews of all integrated external libraries are also advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good technical architecture (7.1) by extending well-audited libraries like LayerZero's OFT and OpenZeppelin's Ownable. Code security (7.2) is generally strong, with… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) is primarily inherited from the LayerZero OFT standard, which handles cross-chain token transfers. The governance model (7.5) is highly centralized, with a single owner… |
| **Upgrades** | 5/10 | Medium | The BridgedFP contract is not designed as an upgradeable proxy (7.7). This means its logic is immutable once deployed, eliminating risks associated with upgrade mechanisms like proxy… |

## Security Findings

_🟡 1 Medium · ⚪ 1 Informational_

### `M-01` — Centralized Control Over Token Metadata  *(Severity: Medium · Status: Unresolved)*

The `BridgedFP` contract allows the `onlyOwner` to update the token's `_updatableName` and `_updatableSymbol` via the `updateName`, `updateSymbol`, and `updateNameAndSymbol` functions. While this provides flexibility for branding or corrections, it introduces a single point of control. A compromised owner key or a malicious owner could change the token's name and symbol to something misleading, potentially causing confusion among users, facilitating phishing attempts, or damaging the project's reputation.

**Recommendation:** Implement robust security practices for the owner's private key, such as using a multi-signature wallet (e.g., Gnosis Safe) for the `_delegate` address. Consider whether the ability to change the name and symbol is strictly necessary post-deployment. If not, these functions could be removed or made immutable after an initial setup period. If dynamic updates are required, ensure clear communication channels are established to inform users of any changes.


### `I-01` — Reliance on External Contracts  *(Severity: Informational · Status: Unresolved)*

The `BridgedFP` contract inherits significant functionality from external, widely-used libraries: `@openzeppelin/contracts/access/Ownable.sol` and `@layerzerolabs/oft-evm/contracts/OFT.sol`. While these libraries are generally considered secure and well-audited, any vulnerability discovered within them could directly impact the security and functionality of the `BridgedFP` contract. This represents a standard dependency risk.

**Recommendation:** Ensure that all external dependencies are kept up-to-date with their latest secure versions. Regularly monitor security advisories and audits related to OpenZeppelin Contracts and LayerZero's OFT library. While direct control over these external contracts is limited, awareness of their security posture is crucial.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd34a...63b7`](https://etherscan.io/address/0xd34a99bc0f67ae1bbd63c660e6d0b0dd03e263b7) |
| **Network** | Ethereum |
| **Price** | $1.1500 |
| **24h Volume** | $787.9K |
| **Liquidity** | $703.7K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 542 buys / 464 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xd6a822d028bbf7b6edfa1533e110ee40c08551d9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/identitymd-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
