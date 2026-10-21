---
token: priceless
ticker: PRICELESS
network: bsc
risk_score: 1
status: low
date: 2026-09-06
---

# priceless (PRICELESS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/priceless-bsc)

---

## Audit Summary

This audit report covers the FourERC20 token contract, an ERC-20 implementation. The analysis is based solely on the provided Solidity source code and prefilled metadata. The contract leverages OpenZeppelin's battle-tested libraries for core ERC-20 functionality, which is a significant strength. However, the contract as provided is incomplete, lacking a public mechanism for token minting or burning, and its metadata requires explicit initialization. These design choices lead to a Medium overall risk level, primarily due to functional limitations if deployed as a standalone token.

> **Final Recommendation:** It is strongly recommended to implement a public supply mechanism (e.g., minting and burning functions with appropriate access control) in a derived contract if this token is intended for practical use. Ensure that the `_init` function is properly called during deployment, either via the constructor of a derived contract or as an initializer in an upgradeable proxy setup, to correctly set the token's name and symbol. Consider adding emergency control mechanisms like pausing functionality to enhance operational security and provide recourse during unforeseen events.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1 Architecture) of the FourERC20 contract is based on standard OpenZeppelin ERC-20 implementations, which provides a robust and secure foundation for core token… |
| **Governance / Economics** | 8/10 | Low | The contract does not implement any specific governance (7.5 Governance) or complex economic (7.4 Economic) models beyond standard ERC-20 token transfers. This simplicity reduces the attack surface… |
| **Upgrades** | 10/10 | Low | The FourERC20 contract is not designed as an upgradeable proxy (7.7 Upgrades) itself. If intended to be used as an implementation contract for an upgradeable proxy, the internal `_init` function… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.9% (≈ permanent lock) |
| **LP Locked** | 99.9% |

## Security Findings

_🟠 2 High · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Incomplete Token Functionality (Missing Supply Mechanism)  *(Severity: High · Status: Unresolved)*

The `FourERC20` contract, as provided, lacks public functions to mint or burn tokens. The `_mint` and `_burn` functions are internal, meaning a derived contract is required to implement the supply mechanism. Without such a derived contract, the token's `_totalSupply` remains zero, and no tokens can be created or distributed, rendering the token non-functional for its intended purpose. This is a critical design oversight if deployed as a standalone token.

**Recommendation:** If this contract is intended to be a deployable token, implement public `mint` and `burn` functions in a derived contract. These functions should include robust access control (e.g., `onlyOwner` or role-based access) to prevent unauthorized supply manipulation. If it's purely a base contract for inheritance, ensure documentation clearly states this requirement.


### `H-02` — Uninitialized Token Metadata and State  *(Severity: High · Status: Unresolved)*

The `_init` function, which is responsible for setting the token's `_name` and `_symbol`, is internal and not called within the `FourERC20` contract's constructor. If this contract is deployed directly, the token's name and symbol will remain uninitialized (empty strings). Furthermore, if this contract is intended to be an implementation for a proxy, the `_init` function must be explicitly called as an initializer to properly set up the token's state. Failure to do so will result in a non-functional token with missing metadata.

**Recommendation:** Ensure that the `_init` function is called during contract deployment. If deploying `FourERC20` directly, add a constructor that calls `_init(name_, symbol_)`. If using a proxy pattern, ensure the proxy's initializer function calls `_init` with the desired name and symbol.


### `L-01` — Absence of Emergency Controls  *(Severity: Low · Status: Unresolved)*

The contract does not include common emergency control mechanisms such as pausing transfers or blacklisting malicious addresses. While not strictly required by ERC-20, these features are often implemented in production tokens to mitigate risks during critical events or security incidents (e.g., major exploits, regulatory demands). The lack of such controls means that in an emergency, the only recourse would be a contract upgrade (if upgradeable) or a complete redeployment.

**Recommendation:** Consider integrating emergency control mechanisms, such as OpenZeppelin's `Pausable` or `AccessControl` contracts, to allow a designated administrator to temporarily halt transfers or restrict specific addresses in critical situations. This enhances operational security and provides a safety net.


### `I-01` — Strong Foundation with OpenZeppelin  *(Severity: Informational · Status: Resolved)*

The contract heavily relies on well-audited OpenZeppelin Contracts (Context, IERC20, IERC20Metadata). This is a significant strength, as it leverages battle-tested code for core ERC-20 functionality. This approach inherently reduces the likelihood of common vulnerabilities like integer overflows/underflows or reentrancy in the standard functions, contributing to a higher overall code security posture.

**Recommendation:** Continue to leverage and stay updated with reputable, audited libraries like OpenZeppelin. Regularly review their updates and security advisories to ensure the project benefits from ongoing improvements and vulnerability fixes.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7d03...4444`](https://bscscan.com/address/0x7d03759e5b41e36899833cb2e008455d69a24444) |
| **Network** | BNB Chain |
| **Price** | $0.0002686 |
| **24h Volume** | $98.5K |
| **Liquidity** | $126.1K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 40.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 780 buys / 464 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x3dc2878f9f60476dbbb18af7531fbe1a603c8dc0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/priceless-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-06*
