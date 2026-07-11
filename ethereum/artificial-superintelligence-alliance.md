---
token: Artificial Superintelligence Alliance
ticker: FET
network: ethereum
risk_score: 66
status: high
date: 2026-06-10
---

# Artificial Superintelligence Alliance (FET) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/artificial-superintelligence-alliance-eth)

---

## Audit Summary

This audit covers the provided Solidity source code for the OpenZeppelin `EnumerableSet` and `Address` libraries. These are foundational utility libraries widely used in the EVM ecosystem. The code exhibits high quality, robust design, and adherence to established best practices. While the prefill suggested a 'FetchToken' contract, the provided source code consists solely of these libraries. The inherent technical risk of these specific libraries is very low, assuming correct integration into consuming contracts.

> **Final Recommendation:** The audited OpenZeppelin `EnumerableSet` and `Address` libraries are robust, well-tested, and secure. Developers integrating these libraries should ensure they are using the latest stable versions where possible and fully understand the implications of functions like `Address.isContract`. It is crucial that consuming contracts correctly handle return values and adhere to secure coding practices when interacting with these libraries to maintain overall system integrity. For projects requiring the highest assurance, a Premium Deploy option is recommended, which includes continuous monitoring and incident response planning post-deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical review (7.1 Architecture, 7.2 Code Security) confirms that the `EnumerableSet` and `Address` libraries are well-structured and implement their intended functionality efficiently and… |
| **Governance / Economics** | 1/10 | High | As utility libraries, `EnumerableSet` and `Address` do not possess inherent governance mechanisms or economic models (7.4 Economic, 7.5 Governance). Therefore, direct governance or economic risks… |
| **Upgrades** | 5/10 | Medium | Libraries in Solidity are generally not upgradeable in the same manner as proxy contracts (7.7 Upgrades). Once deployed, their code is immutable. Any 'upgrade' would involve deploying new versions of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 87.1% |
| **Top-3 Unlocked** | ⚠️ 95.8% |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Older Solidity Compiler Version Used  *(Severity: Informational · Status: Unresolved)*

The contract uses `pragma solidity 0.6.2`. While functional, newer Solidity compiler versions (e.g., 0.8.x) introduce significant security enhancements, such as default checked arithmetic for `uint256` operations, improved optimizer, and more explicit error handling. Using an older version might expose the code to subtle vulnerabilities that newer compilers mitigate by default.

**Recommendation:** Consider upgrading to a more recent and actively maintained Solidity compiler version (e.g., 0.8.x) to benefit from the latest security features and optimizations. Ensure thorough testing if an upgrade is performed.


### `I-02` — `Address.isContract` Limitations Awareness  *(Severity: Informational · Status: Unresolved)*

The `Address.isContract` function, while correctly implemented and documented within the library, has inherent limitations. It returns `false` for externally-owned accounts (EOAs), contracts in construction, addresses where a contract will be created, or addresses where a contract lived but was destroyed. Developers using this function in consuming contracts (7.3 Access Control, 7.6 External) must be fully aware of these nuances to avoid incorrect assumptions about account types, which could lead to unintended access control bypasses or logic errors.

**Recommendation:** Ensure that any consuming contracts relying on `Address.isContract` are designed with a full understanding of its limitations. Avoid making critical security decisions solely based on its return value without additional checks or context. Document these considerations clearly in the consuming contract's design.


### `I-03` — General Library Usage Best Practices  *(Severity: Informational · Status: Unresolved)*

The provided code consists of well-audited and robust OpenZeppelin libraries. The overall security and integrity of a system (7.2 Code Security, 7.8 Operations) heavily depend on how these libraries are integrated and utilized by the consuming contracts. Incorrect usage patterns, such as not handling return values from `add` or `remove` functions, improper type casting, or misunderstanding the state changes, could introduce vulnerabilities in the calling contract, even if the library itself is secure.

**Recommendation:** Developers of consuming contracts should adhere to best practices for library integration. This includes carefully reviewing library documentation, handling all return values, performing necessary input validation, and conducting comprehensive unit and integration testing of all interactions with these libraries.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xaea4...ad85`](https://etherscan.io/address/0xaea46a60368a7bd060eec7df8cba43b7ef41ad85) |
| **Network** | Ethereum |
| **Price** | $0.2676 |
| **24h Volume** | $301.0K |
| **Liquidity** | $1.75M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 3y |
| **Top-10 Holders** | 50.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 180 buys / 151 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Artificial Superintelligence Alliance a scam?

The contract for Artificial Superintelligence Alliance (FET) is verified and its ownership has been renounced, which are positive indicators for transparency and reduced centralized control. While these steps mitigate some fundamental scam risks, investors should still consider other high-risk factors identified, such as token concentration and unlocked liquidity, to form a comprehensive view of its investment profile.

### Is Artificial Superintelligence Alliance safe to buy?

Given the high-risk score of 65/100, FET presents notable safety concerns for investors. Key factors include the top 10 holders controlling 50.1% of the supply, creating significant centralization risk. Furthermore, the liquidity is not locked, exposing investors to potential rug pull scenarios where liquidity could be suddenly withdrawn. The existence of a mint function also introduces inflationary potential.

### Has Artificial Superintelligence Alliance been audited?

The FET token contract has been verified, confirming its source code matches the deployed code on the blockchain for transparency. This allows public inspection of its functionality. However, contract verification is not the same as a comprehensive security audit by an independent third party, which thoroughly assesses for vulnerabilities and potential exploits.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x948b54a93f5ad1df6b8bff6dc249d99ca2eca052)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/artificial-superintelligence-alliance-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
