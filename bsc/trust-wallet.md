---
token: Trust Wallet
ticker: TWT
network: bsc
risk_score: 45
status: medium
date: 2026-09-02
---

# Trust Wallet (TWT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trust-wallet-bsc)

---

## Audit Summary

The provided code implements a standard ERC20 token with burnable functionality, largely based on OpenZeppelin contracts. While it correctly uses `SafeMath` to prevent integer overflows/underflows, a critical functional flaw exists: there is no mechanism to mint new tokens, rendering the `_totalSupply` permanently zero and making the token unusable. This fundamental issue prevents the token from serving its intended purpose.

> **Final Recommendation:** It is strongly recommended to address the critical functional flaw regarding token minting. A public or owner-restricted minting function must be implemented in a derived contract to allow for token creation and distribution. Additionally, consider implementing a mechanism to mitigate the ERC20 `approve` race condition, such as the `approve(0)` pattern. Ensure that any future extensions or integrations are thoroughly reviewed for potential security implications.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1) is a standard ERC20 implementation, leveraging battle-tested OpenZeppelin patterns and `SafeMath` for robust arithmetic operations (7.2 Code Security). However, a… |
| **Governance / Economics** | 1/10 | High | The contract, as a standalone ERC20 token, lacks explicit governance mechanisms (7.5). Economically (7.4), the token's design is fundamentally flawed as no tokens can ever be minted, meaning the… |
| **Upgrades** | 6/10 | Medium | The contract is not designed to be upgradeable (7.7), which eliminates upgrade-specific risks such as proxy storage collisions or logic errors during upgrades. However, this also means that any… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.3% |
| **Top-3 Unlocked** | ⚠️ 99.8% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — No Minting Mechanism  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_mint` function is declared as `internal virtual` but is not called by any public or external function within the provided `ERC20` or `ERC20Burnable` contracts. This means that no tokens can ever be created, and the `_totalSupply` will perpetually remain zero. Consequently, the token cannot be distributed or used for any intended purpose, rendering the contract non-functional.

**Recommendation:** Implement a public or owner-restricted minting function in a derived contract that calls `_mint(address account, uint256 amount)` to allow for the creation and initial distribution of tokens. Ensure appropriate access control (e.g., `onlyOwner`) is applied to prevent unauthorized token inflation.


### `L-01` — ERC20 `approve` Race Condition  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The standard ERC20 `approve` function is susceptible to a known front-running vulnerability. If a user attempts to change an allowance from a non-zero value to another non-zero value, a malicious actor could front-run the transaction, spend the original allowance, and then spend the newly approved allowance, effectively spending more than the user intended.

**Recommendation:** While this is a known ERC20 standard limitation, consider implementing a two-step approval process (e.g., setting allowance to zero before setting a new value) or using `increaseAllowance`/`decreaseAllowance` functions where possible, which are less susceptible to this specific race condition.


### `I-01` — Older Solidity Compiler Version  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is compiled with Solidity version 0.6.12. While `SafeMath` is used to mitigate integer overflow/underflow issues, newer compiler versions (e.g., 0.8.x and above) include built-in overflow and underflow checks by default, reducing reliance on external libraries for this specific security concern. Newer versions also offer other optimizations and security improvements.

**Recommendation:** Consider upgrading to a more recent Solidity compiler version (e.g., 0.8.x) to benefit from built-in safety checks and other language improvements. If upgrading, ensure all arithmetic operations are reviewed as `SafeMath` would no longer be strictly necessary for overflow/underflow prevention.


### `I-02` — Empty `_beforeTokenTransfer` Hook  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_beforeTokenTransfer` hook is an empty virtual function. While this is a common pattern for extensibility, it currently serves no functional purpose within the provided contracts. If custom logic (e.g., blacklisting, fees, snapshotting) is intended to be executed before or after token transfers, it would need to be implemented in a derived contract.

**Recommendation:** If no custom logic is required for token transfers, this is acceptable. If future functionality is planned, ensure that any overrides of this hook in derived contracts are thoroughly tested and do not introduce new vulnerabilities or unexpected behavior.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4b0f...8003`](https://bscscan.com/address/0x4b0f1812e5df2a09796481ff14017e6005508003) |
| **Network** | BNB Chain |
| **Price** | $0.5938 |
| **24h Volume** | $302.0K |
| **Liquidity** | $616.7K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 3y |
| **Top-10 Holders** | 80.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 996 buys / 943 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x8ccb4544b3030dacf3d4d71c658f04e8688e25b1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trust-wallet-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
