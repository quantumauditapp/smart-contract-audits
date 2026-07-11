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

This audit covers the provided Solidity source code for the EnumerableSet and Address utility libraries. These libraries, originating from OpenZeppelin, are foundational components designed for efficient data management and address utility functions. The code exhibits high quality, robust design, and adherence to best practices. No critical or high-severity vulnerabilities were identified. The prefill indicated 'FetchToken' as the contract name, but the provided source code is for these libraries.

> **Final Recommendation:** The provided EnumerableSet and Address libraries are highly secure and well-engineered. For future development, consider migrating to newer Solidity compiler versions (e.g., 0.8.x) to leverage built-in safety features like overflow checks and reduce potential compatibility issues with newer tools and best practices. Ensure that any contracts integrating these libraries are thoroughly audited, paying close attention to how they manage state, access control, and external interactions, as these are the primary vectors for vulnerabilities in application-specific logic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture of the EnumerableSet and Address libraries is highly robust and well-optimized. EnumerableSet provides O(1) operations for add, remove, contains, and length, utilizing a… |
| **Governance / Economics** | 1/10 | High | These libraries do not implement any direct governance mechanisms (7.5 Governance) or economic models (7.4 Economic). Their function is purely utility-based, providing data structures and… |
| **Upgrades** | 5/10 | Medium | Libraries in Solidity are immutable once deployed and cannot be upgraded (7.7 Upgrades). Contracts that use these libraries are compiled with the library's bytecode linked, meaning any changes to the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 87.1% |
| **Top-3 Unlocked** | ⚠️ 95.8% |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Older Solidity Compiler Version  *(Severity: Informational · Status: Unresolved)*

The contract uses Solidity version 0.6.2. While functional, newer versions (e.g., 0.8.x) include built-in overflow/underflow checks for `uint` types, reducing the need for `SafeMath` or similar libraries. They also offer other language improvements and bug fixes.

**Recommendation:** Consider upgrading to a more recent Solidity compiler version (e.g., 0.8.x) to benefit from enhanced security features and improved developer experience. Thoroughly test all contract logic after any compiler upgrade.


### `I-02` — `Address.isContract` Limitations (Documented)  *(Severity: Informational · Status: Unresolved)*

The `Address.isContract` function, while useful, has known limitations as explicitly documented within the library itself. It may return `false` for contracts under construction, addresses where a contract will be created, or addresses where a contract was destroyed. Relying solely on `isContract` to distinguish between EOAs and contracts can lead to incorrect assumptions.

**Recommendation:** Users of `Address.isContract` should be fully aware of its limitations and avoid making critical security decisions based solely on its return value. For robust contract interaction checks, consider alternative methods or multi-factor verification where applicable.


### `I-03` — Non-Guaranteed Element Order in EnumerableSet  *(Severity: Informational · Status: Unresolved)*

The `EnumerableSet` library explicitly states that 'No guarantees are made on the ordering' of elements, and the order 'may change when more values are added or removed.' This is a consequence of the 'swap and pop' optimization used for O(1) removals, which reorders elements to maintain efficiency.

**Recommendation:** Developers utilizing `EnumerableSet` must not rely on the order of elements when iterating or accessing them via the `at(index)` function. If a specific order is required, an alternative data structure or an additional mapping to maintain order should be implemented by the consuming contract.

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
