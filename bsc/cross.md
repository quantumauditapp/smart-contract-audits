---
token: Cross
ticker: CROSS
network: bsc
risk_score: 53
status: high
date: 2026-08-13
---

# Cross (CROSS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 53/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cross-bsc)

---

## Audit Summary

The CrossToken contract implements a standard ERC20 token with burnable and permit functionalities, leveraging battle-tested OpenZeppelin libraries. The technical implementation is robust, with no apparent critical vulnerabilities. However, the contract design introduces centralization risks due to the owner's exclusive control over the burn function and the use of an EOA for ownership, which could impact token economics and governance if compromised or misused.

> **Final Recommendation:** It is strongly recommended to transfer ownership of the `CrossToken` contract to a robust multi-signature wallet (e.g., Gnosis Safe). This would distribute control over critical functions like `burn` among multiple trusted parties, significantly mitigating the risk associated with a single point of failure (EOA ownership). Additionally, consider clearly communicating the implications of the owner-controlled burn function to token holders to ensure transparency regarding potential supply adjustments and maintain trust within the community.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The `CrossToken` contract is built upon battle-tested OpenZeppelin ERC20, ERC20Burnable, ERC20Permit, and Ownable libraries, ensuring a high degree of code security and adherence to ERC standards… |
| **Governance / Economics** | 1/10 | High | The primary economic and governance risk stems from the centralized control over the token's `burn` function, which is restricted to the contract owner (7.4 Economic). This allows a single entity to… |
| **Upgrades** | 6/10 | Medium | The `CrossToken` contract is not designed with upgradeability in mind (7.7 Upgrades). It is deployed as an immutable contract, meaning its logic cannot be altered post-deployment. While this… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 1 Informational_

### `H-01` — Centralized Control Over Token Supply via Burn Function  *(Severity: High · Status: Unresolved)*

The `burn` function in the `CrossToken` contract is protected by the `onlyOwner` modifier. This grants the contract owner exclusive power to reduce the total supply of tokens at any time. While this can be a desired feature for supply management, it introduces a significant centralization risk (7.4 Economic). A malicious or compromised owner could burn a substantial amount of tokens, leading to a drastic devaluation or even a rug pull scenario for token holders.

**Recommendation:** If the ability to burn tokens is essential, consider implementing a more decentralized approach, such as requiring a multi-signature approval for burn operations or integrating a time-lock mechanism. Alternatively, if the owner's control is intentional, ensure robust security measures for the owner's private key and transparently communicate this capability to the community.


### `M-01` — Single Point of Failure Due to EOA Ownership  *(Severity: Medium · Status: Unresolved)*

The `CrossToken` contract is currently owned by an External Owned Account (EOA) (7.5 Governance). This creates a single point of failure, as the security of the entire contract's administrative functions (including the ability to burn tokens) relies solely on the security of that single EOA's private key. If this EOA is compromised, an attacker could gain full control over the owner-restricted functions, leading to potential misuse and loss of funds.

**Recommendation:** Transfer ownership of the contract to a multi-signature wallet (e.g., Gnosis Safe). A multi-sig wallet requires multiple independent approvals for transactions, significantly enhancing security by distributing control and reducing the risk associated with a single compromised key.


### `I-01` — Immutability of Contract Logic  *(Severity: Informational · Status: Unresolved)*

The `CrossToken` contract is deployed directly and does not implement any upgradeability mechanism (7.7 Upgrades). This means that once deployed, the contract's logic cannot be modified. While this eliminates risks associated with upgrade mechanisms (e.g., proxy vulnerabilities), it also implies that any discovered bugs or desired feature enhancements would necessitate deploying an entirely new contract and migrating all token holders, which can be a complex and costly process.

**Recommendation:** This is a design choice. If immutability is intended, no action is required. If future flexibility is desired, consider implementing an upgradeable proxy pattern (e.g., UUPS) for future deployments, though this adds complexity and its own set of risks.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6bf6...a510`](https://bscscan.com/address/0x6bf62ca91e397b5a7d1d6bce97d9092065d7a510) |
| **Network** | BNB Chain |
| **Price** | $0.1014 |
| **24h Volume** | $914.5K |
| **Liquidity** | $1.05M |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 97.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3469 buys / 3831 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xe6e51ea572502dbdf8b40834d0619f9a9144d3a5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cross-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
