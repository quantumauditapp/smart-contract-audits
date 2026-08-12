---
token: 我踏马来了
ticker: 我踏马来了
network: bsc
risk_score: 18
status: low
date: 2026-08-12
---

# 我踏马来了 (我踏马来了) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 18/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-6e44cf-bsc)

---

## Audit Summary

The FourERC20 contract implements a standard ERC-20 token, largely leveraging well-audited OpenZeppelin Contracts. The core functionality for transfers and allowances is robust. However, the token's metadata (name and symbol) is not initialized within the contract, and there are no public minting or burning mechanisms, indicating a fixed supply model unless extended by a derived contract. The overall technical risk is low due to the use of battle-tested libraries, but deployment considerations for metadata initialization are important.

> **Final Recommendation:** It is recommended to ensure that the `_init` function is properly called in a constructor of a derived contract or during deployment to set the token's name and symbol, ensuring full ERC-20 compliance and usability. For any future extensions, carefully consider the implementation of minting/burning mechanisms with appropriate access control. Thoroughly test any integrations with external protocols to ensure compatibility and security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract (7.1 Architecture, 7.2 Code Security) is built upon OpenZeppelin's battle-tested ERC-20 implementation (v4.9.4), which provides a strong foundation for security, including robust… |
| **Governance / Economics** | 5/10 | Medium | The FourERC20 contract (7.4 Economic, 7.5 Governance) does not implement any governance mechanisms or explicit owner roles, aligning with the prefill information that ownership is renounced. The… |
| **Upgrades** | 9/10 | Low | The contract (7.7 Upgrades) is not designed with an upgrade proxy pattern, meaning it is immutable once deployed. This eliminates upgrade-related risks such as proxy misconfigurations or logic errors… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 53.1% |
| **Top-3 Unlocked** | ⚠️ 95.5% |

## Security Findings

_🟢 1 Low · ⚪ 3 Informational_

### `L-01` — Uninitialized Token Metadata  *(Severity: Low · Status: Unresolved)*

The `_init` function, which is responsible for setting the token's `_name` and `_symbol`, is declared as `internal` but is not called by a constructor within the `FourERC20` contract. If `FourERC20` is deployed directly without a derived contract calling `_init` in its constructor, the token's name and symbol will remain empty strings. This impacts the token's usability and display in wallets and explorers, potentially causing confusion or misrepresentation.

**Recommendation:** Implement a constructor in `FourERC20` or a derived contract that calls `_init(string memory name_, string memory symbol_)` to ensure the token's metadata is properly set upon deployment. For example: ```solidity constructor(string memory name_, string memory symbol_) {     _init(name_, symbol_); } ```


### `I-01` — Reliance on OpenZeppelin Standard Implementation  *(Severity: Informational · Status: Resolved)*

The `FourERC20` contract is largely based on the OpenZeppelin Contracts (v4.9.4) ERC-20 implementation. This foundation provides a high degree of security due to extensive audits, community review, and battle-testing of the OpenZeppelin library, significantly reducing the likelihood of common vulnerabilities like reentrancy or integer overflows.

**Recommendation:** Continue to leverage well-audited and maintained libraries like OpenZeppelin. Ensure that any custom logic added to derived contracts maintains the same high security standards.


### `I-02` — Fixed Supply Mechanism (in FourERC20)  *(Severity: Informational · Status: Unresolved)*

The `FourERC20` contract, as provided, does not expose any public functions for minting or burning tokens. The `_mint` and `_burn` functions are internal, meaning that the total supply of the token is fixed after its initial deployment (assuming an initial mint is performed in a constructor or derived contract). This design choice impacts the token's economic model and prevents dynamic supply adjustments without further contract extensions.

**Recommendation:** Clearly document the intended supply mechanism (fixed, capped, or elastic) for the token. If a dynamic supply is desired, a derived contract must implement and expose minting/burning functions with appropriate access control (e.g., using `Ownable` or a governance mechanism).


### `I-03` — Unused `_contextSuffixLength` Function  *(Severity: Informational · Status: Resolved)*

The `_contextSuffixLength()` function, inherited from the `Context` contract, is present in `FourERC20` but returns 0 and is not explicitly utilized within the contract's logic. While harmless, it represents a minor piece of unused code from the inherited library.

**Recommendation:** No action is strictly required as this is part of the OpenZeppelin library's design for potential meta-transaction handling. It can be ignored or, if desired, the `Context` contract could be replaced with a more minimal version if meta-transaction support is not needed and gas optimization is critical.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc51a...4444`](https://bscscan.com/address/0xc51a9250795c0186a6fb4a7d20a90330651e4444) |
| **Network** | BNB Chain |
| **Price** | $0.008793 |
| **24h Volume** | $206.1K |
| **Liquidity** | $726.6K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 87.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 653 buys / 784 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xa651c8deb3ff9f8d56a26e72042b7a8a1f433480)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-6e44cf-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
