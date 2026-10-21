---
token: Messier
ticker: M87
network: ethereum
risk_score: 73
status: high
date: 2026-09-12
---

# Messier (M87) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 73/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/messier-eth)

---

## Audit Summary

The audit of the M87 contract is severely limited as the source code for the main contract (M87) was not provided, only its interfaces and a utility library. This prevents any meaningful technical security analysis. Based on available metadata, significant economic and governance risks are identified, including centralized control by an EOA and unlocked liquidity pools. Users are strongly advised against interacting with this contract without full source code verification and a comprehensive audit.

> **Final Recommendation:** Given the critical absence of the main contract's source code, it is strongly recommended to avoid any interaction with this contract. If the project intends to be trustworthy, the full source code for the M87 contract must be published and undergo a thorough security audit. Additionally, the project owner should consider renouncing ownership to a timelock or a multi-signature wallet to decentralize control and lock liquidity permanently or for a significant duration to mitigate rug pull risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Due to the absence of the M87 contract's source code, a comprehensive technical security assessment (7.1 Architecture, 7.2 Code Security, 7.3 Access Control) could not be performed. The provided… |
| **Governance / Economics** | 2/10 | High | The contract exhibits high governance and economic risks. Ownership is retained by an External Owned Account (EOA) (7.5 Governance), allowing centralized control over critical functions. Furthermore… |
| **Upgrades** | 6/10 | Medium | The contract is not implemented as a proxy (7.7 Upgrades), meaning it is not upgradeable. While this eliminates risks associated with upgrade mechanisms (e.g., proxy initialization, storage… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 99.5% — Null Address, UNCX |
| **Top-1 Unlocked Holder** | 0.5% |
| **Lock Expiry** | Expired 134d ago |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Missing Source Code for Core Contract  *(Severity: Critical · Status: Unresolved)*

The source code for the main contract, M87 (0x80122c6a83c8202ea365233363d3f4837d13e888), was not provided for audit. Only interfaces and a utility library were available. This prevents any technical verification of the contract's logic, security mechanisms, access controls, and adherence to best practices. Without the source code, the contract is unauditable, and its behavior cannot be guaranteed.

**Recommendation:** Publish the complete and verified source code for the M87 contract on a public block explorer (e.g., Etherscan) to allow for full transparency and a comprehensive security audit.


### `H-01` — Centralized Control by EOA  *(Severity: High · Status: Unresolved)*

The contract's ownership is retained by an External Owned Account (EOA) (0xb3067cb8d2bc718cb34e772dd389f3e7809253eb). This centralized control allows a single entity to potentially execute critical functions, modify parameters, or even drain funds if such functionalities are present in the unaudited M87 contract. This poses a single point of failure and a significant trust requirement on the owner.

**Recommendation:** Transfer ownership to a multi-signature wallet (e.g., Gnosis Safe) with a sufficient number of signers or a time-locked contract to decentralize control and introduce a delay for critical operations, enhancing security and trust.


### `H-02` — Unlocked Liquidity Pool  *(Severity: High · Status: Unresolved)*

According to the provided metadata, the liquidity pool (LP) associated with the M87 token is reported as 'lock_expired'. This indicates that the LP tokens are no longer locked and can be withdrawn by the owner or designated address at any time. This creates a significant 'rug pull' risk, where the liquidity can be removed, rendering the token worthless.

**Recommendation:** Lock the liquidity pool tokens for a substantial period (e.g., several years) using a reputable locker service (e.g., UNCX Network, Pinksale) to assure investors of long-term liquidity and mitigate rug pull concerns.


### `M-01` — Lack of Emergency Measures  *(Severity: Medium · Status: Unresolved)*

Without the M87 contract's source code, it is impossible to verify if any emergency functions (e.g., pause, circuit breaker, emergency withdrawal) are implemented. In the event of a critical vulnerability or exploit, the absence of such mechanisms could lead to irreversible loss of funds or protocol disruption.

**Recommendation:** Implement and clearly document emergency functions, such as a pause mechanism to halt critical operations, or an emergency withdrawal function to allow users to retrieve funds in case of a severe incident. These functions should ideally be controlled by a multi-signature wallet or a governance mechanism.


### `L-01` — No Upgradeability  *(Severity: Low · Status: Unresolved)*

The contract is not deployed as a proxy, meaning it is not upgradeable. While this eliminates risks associated with complex upgrade mechanisms (e.g., proxy initialization, storage collisions), it also means that any bugs or vulnerabilities discovered post-deployment cannot be fixed without deploying an entirely new contract and migrating users/assets.

**Recommendation:** For non-upgradeable contracts, ensure extremely rigorous testing and auditing before deployment, as the code is immutable. If future feature enhancements or bug fixes are anticipated, consider a well-vetted proxy pattern for future deployments.


### `I-01` — Reliance on External Uniswap Interfaces  *(Severity: Informational · Status: Unresolved)*

The provided source code includes interfaces for Uniswap V2 Factory, Pair, and Router contracts, as well as standard ERC20 interfaces. This indicates that the M87 contract likely interacts with the Uniswap ecosystem for liquidity provision or token swapping. While these interfaces are standard and well-vetted, the contract's reliance on external protocols introduces dependency risks.

**Recommendation:** Ensure that all external contract addresses used by M87 are correctly configured and verified. Implement robust error handling for external calls and consider mechanisms to mitigate risks from potential issues in dependent protocols, although Uniswap V2 is highly stable.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8012...e888`](https://etherscan.io/address/0x80122c6a83c8202ea365233363d3f4837d13e888) |
| **Network** | Ethereum |
| **Price** | $0.00001178 |
| **24h Volume** | $103.8K |
| **Liquidity** | $977.5K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 34.3% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 197 buys / 117 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x2049df3435bdbb36d22f98fcd2e5027049a1f3ce)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/messier-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
