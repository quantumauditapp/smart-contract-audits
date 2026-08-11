---
token: Subsquid
ticker: SQD
network: bsc
risk_score: 60
status: high
date: 2026-08-11
---

# Subsquid (SQD) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 60/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/subsquid-bsc)

---

## Audit Summary

The PeerToken contract is an ERC-20 token with minting and burning capabilities, leveraging OpenZeppelin's audited libraries. The primary risks identified stem from the highly centralized control over token supply and administrative functions, particularly the unlimited minting power held by a single `minter` address, which is itself controlled by a single `owner` address. While the code quality is high due to OpenZeppelin's robust implementations, the economic model introduces significant centralization risks.

> **Final Recommendation:** To mitigate the identified risks, consider implementing a multi-signature wallet for both the `owner` and `minter` roles to distribute control and reduce the risk of a single point of failure. Evaluate the necessity of unlimited minting; if a fixed supply or a capped minting schedule is desired, implement these restrictions directly within the contract logic. For future projects, assess the trade-offs between immutability and upgradeability, potentially using a proxy pattern if flexibility for bug fixes or feature enhancements is critical.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract is well-structured, inheriting from standard OpenZeppelin ERC20, ERC20Burnable, and Ownable contracts (7.1 Architecture). It correctly implements access control modifiers (`onlyMinter`… |
| **Governance / Economics** | 1/10 | High | The economic model presents a critical risk due to the centralized minting authority. A single `minter` address, controlled by the `owner`, can mint an unlimited supply of tokens, posing a… |
| **Upgrades** | 5/10 | Medium | The PeerToken contract is implemented as a standard, non-upgradeable contract. This design choice eliminates risks associated with proxy patterns or upgrade mechanisms, such as storage collisions or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Centralized Minting Authority and Unlimited Supply  *(Severity: Critical · Status: Unresolved)*

The `minter` role, which is controlled by the `owner`, has the ability to mint an arbitrary amount of tokens without any on-chain supply cap. This poses a critical economic risk (7.4 Economic), as a compromised `minter` or `owner` key could lead to hyperinflation and severe devaluation of the token. The contract does not enforce any maximum total supply.

**Recommendation:** Implement a multi-signature wallet for the `minter` role. Consider adding a hard cap on the total supply of tokens or implementing a controlled minting schedule to limit the potential for inflation. If unlimited minting is a core design choice, ensure robust operational security for the `minter` and `owner` keys.


### `H-01` — High Centralization of Administrative Control  *(Severity: High · Status: Unresolved)*

The `Ownable` pattern grants significant administrative power to a single `owner` address, specifically the ability to `setMinter` and `transferOwnership` (7.3 Access Control). This central point of failure increases operational risk (7.8 Operations), as a compromised `owner` key could lead to unauthorized changes in the `minter` role, loss of administrative control, or other malicious actions.

**Recommendation:** Implement a multi-signature wallet for the `owner` address to distribute control and reduce the risk associated with a single point of failure. This would require multiple approvals for critical administrative actions, enhancing security.


### `L-01` — Immutability of Contract Logic  *(Severity: Low · Status: Unresolved)*

The `PeerToken` contract is not upgradeable (7.7 Upgrades). While this eliminates risks associated with upgrade mechanisms, it means that any discovered vulnerabilities or desired feature changes would necessitate a new contract deployment and a potentially complex and costly migration of assets and user base. This lack of flexibility can be a long-term operational challenge.

**Recommendation:** Acknowledge the implications of immutability. For future projects, if flexibility for bug fixes or feature enhancements is critical, consider implementing an upgradeable proxy pattern (e.g., UUPS) to allow for future contract logic updates without redeployment.


### `I-01` — Single Address for Minter Role  *(Severity: Informational · Status: Unresolved)*

The `minter` role is assigned to a single external address. While this is functional, for systems requiring higher security or distributed control, relying on a single address for such a powerful role can be a point of concern (7.3 Access Control, 7.8 Operations).

**Recommendation:** Consider using a multi-signature wallet or a more robust role-based access control (RBAC) system (e.g., OpenZeppelin's `AccessControl` contract) for the `minter` role to enhance security and decentralize control, if appropriate for the project's long-term vision.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe50e...cc13`](https://bscscan.com/address/0xe50e3d1a46070444f44df911359033f2937fcc13) |
| **Network** | BNB Chain |
| **Price** | $0.04373 |
| **24h Volume** | $3.37M |
| **Liquidity** | $466.4K |
| **Volume / Liquidity** | 7.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 92.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 20936 buys / 23573 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x43256d0dcc2571e564311edb6d7e8f076a72fc46)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/subsquid-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
