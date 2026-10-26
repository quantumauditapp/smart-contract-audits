---
token: Gstock
ticker: GSTOCK
network: bsc
risk_score: 9
status: low
date: 2026-09-22
---

# Gstock (GSTOCK) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gstock-bsc)

---

## Audit Summary

The GeniusLauncherToken contract is a standard ERC20 token with burnable functionality, leveraging battle-tested OpenZeppelin libraries. The contract is simple, primarily focused on token creation and immutable metadata storage. No critical or high-severity vulnerabilities were identified. Informational findings highlight design choices regarding metadata immutability and centralized initial supply distribution. A low-severity finding notes the absence of emergency control mechanisms.

> **Final Recommendation:** The GeniusLauncherToken contract is well-implemented and utilizes established OpenZeppelin standards, resulting in a low overall risk profile. It is recommended to ensure the 'curve' address, which receives the initial token supply, is secured with robust multi-signature or hardware wallet protection. Project teams should also be aware of the immutable nature of the token's metadata and plan accordingly for any future branding or information updates.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1) is straightforward, implementing a standard ERC20 token with burn functionality using OpenZeppelin contracts, which are widely audited and secure. Code security (7.2)… |
| **Governance / Economics** | 4/10 | Medium | The economic model (7.4) is that of a simple ERC20 token, with the entire initial supply minted to a designated 'curve' address. This centralizes initial distribution, making the security of the… |
| **Upgrades** | 6/10 | Medium | The GeniusLauncherToken contract is not designed to be upgradeable (7.7). It does not implement any proxy patterns (e.g., UUPS, Transparent). This eliminates risks associated with upgrade mechanisms… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 16.4% |
| **Top-3 Unlocked** | 30.0% |

## Security Findings

_🟢 1 Low · ⚪ 2 Informational_

### `L-01` — Lack of Emergency Control Mechanisms  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `GeniusLauncherToken` contract, being a standard ERC20, does not include common emergency control features such as `pause` or `blacklist` functionality. In the event of a critical vulnerability, exploit, or regulatory requirement, there would be no built-in mechanism to halt transfers or restrict malicious actors. While this promotes decentralization, it removes a potential safety net for unforeseen circumstances.

**Recommendation:** Consider implementing an `Ownable` or `AccessControl` pattern to allow a designated role (e.g., `pauser`) to pause token transfers in emergencies. This adds a layer of protection, though it introduces a point of centralization. If decentralization is paramount, this finding can be accepted as a design choice.


### `I-01` — Immutability of Token Metadata  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The token's metadata, including `logo`, `description`, and the `_socials` struct, is set exclusively in the constructor and stored as immutable state variables. This means that once the contract is deployed, this information cannot be updated or modified. Any changes to project branding, social links, or descriptions would necessitate the deployment of an entirely new token contract.

**Recommendation:** Ensure that the project team is fully aware of the immutable nature of this metadata. If future updates are anticipated, consider a design where metadata is stored in an upgradeable contract or an off-chain registry referenced by a mutable URI, though this adds complexity and external dependencies.


### `I-02` — Centralized Initial Supply Distribution  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The entire initial token supply (`supply_`) is minted to the `curve_` address during the contract's deployment. This design choice makes the `curve_` address a single point of control for the initial distribution and management of the token supply. The security and operational integrity of this specific address are paramount for the token's initial launch and subsequent distribution strategy.

**Recommendation:** Ensure that the `curve_` address is secured with the highest level of protection, such as a multi-signature wallet, hardware wallet, or a robust access control system. Implement strict operational procedures for managing this address to mitigate risks associated with private key compromise or unauthorized access.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcafd...9e20`](https://bscscan.com/address/0xcafdbce93477261db8250e42bdae6e66733f9e20) |
| **Network** | BNB Chain |
| **Price** | $0.02889 |
| **24h Volume** | $3.84M |
| **Liquidity** | $491.5K |
| **Volume / Liquidity** | 7.8× |
| **Token Age** | 4d |
| **Top-10 Holders** | 19.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4874 buys / 3379 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x7a907a283ef913eb25bee3afd110f687a3fb7eed)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gstock-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-22*
