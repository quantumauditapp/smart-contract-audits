---
token: Zcash Token
ticker: ZEC
network: bsc
risk_score: 73
status: high
date: 2026-09-12
---

# Zcash Token (ZEC) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 73/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zcash-token-bsc)

---

## Audit Summary

The BEP20Zcash contract implements a standard BEP-20 token with `Ownable` access control and `SafeMath` for arithmetic operations. The code is generally well-structured and addresses common integer overflow/underflow issues. However, the contract utilizes an outdated Solidity compiler version and features a centralized minting capability, which introduces a medium level of economic and technical risk. Minor code quality improvements are also recommended.

> **Final Recommendation:** It is strongly recommended to upgrade the Solidity compiler to a more recent, stable version (e.g., 0.8.x) to benefit from the latest security features and optimizations. The centralized minting capability should be carefully considered; if not strictly necessary, it could be removed, or its control could be decentralized through a multi-signature wallet or a time-locked governance mechanism. Additionally, a thorough review of the codebase to remove unused functions and redundant code will improve clarity and reduce gas costs.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates solid technical foundations, utilizing the `SafeMath` library to prevent common integer overflow/underflow vulnerabilities (7.2 Code Security). It implements the BEP-20… |
| **Governance / Economics** | 1/10 | High | The economic model is straightforward, with a fixed initial supply and standard BEP-20 token transfers (7.4 Economic). The `Ownable` pattern provides clear access control for critical functions, such… |
| **Upgrades** | 3/10 | High | This contract is not designed with an upgrade mechanism, meaning its logic is immutable once deployed (7.7 Upgrades). This provides certainty regarding the contract's behavior over its lifetime.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 33.7% |
| **Top-3 Unlocked** | 63.2% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Centralized Minting Capability  *(Severity: Medium · Status: Unresolved)*

The `mint` function is restricted to the contract owner via the `onlyOwner` modifier. This grants the owner the unilateral ability to increase the total token supply at any time. This centralization introduces a significant economic risk, as a compromised owner key or a malicious owner could lead to arbitrary inflation, devaluing existing token holders' assets (7.3 Access Control, 7.4 Economic).

**Recommendation:** Consider if the minting capability is strictly necessary. If so, implement a more decentralized control mechanism, such as a multi-signature wallet for the owner address, a time-locked minting schedule, or a community governance system. If not essential, remove the `mint` function entirely to establish a fixed supply.


### `M-02` — Outdated Solidity Compiler Version  *(Severity: Medium · Status: Unresolved)*

The contract is compiled with Solidity version `0.5.16`. While `SafeMath` mitigates common integer issues, older compiler versions may lack recent security patches, optimizations, or introduce subtle vulnerabilities that have been addressed in newer versions (e.g., 0.8.x series). Using an outdated compiler can expose the contract to known or undiscovered compiler-level bugs (7.2 Code Security).

**Recommendation:** Upgrade the Solidity compiler to a more recent, stable version (e.g., 0.8.x). This would require careful testing and adaptation of the code, especially regarding `SafeMath` (which is often no longer needed in 0.8.x due to default overflow/underflow checks) and other syntax changes.


### `L-01` — Standard ERC-20 `approve` Race Condition  *(Severity: Low · Status: Unresolved)*

The `approve` function is susceptible to a known ERC-20 front-running vulnerability. If a user calls `approve(spender, newAmount)` while the `spender` is concurrently trying to `transferFrom` an existing allowance, the `spender` might be able to spend both the old and new allowance. While the contract includes `increaseAllowance` and `decreaseAllowance` which mitigate this for users who utilize them, direct `approve` calls remain vulnerable (7.2 Code Security).

**Recommendation:** Educate users to primarily use `increaseAllowance` and `decreaseAllowance` instead of directly calling `approve` when modifying an existing allowance. For new allowances, `approve` is safe. This is a common ERC-20 pattern, and the provided mitigation functions are good practice.


### `I-01` — Unused Code and Redundant Function  *(Severity: Informational · Status: Unresolved)*

The contract contains several pieces of code that are either unused or redundant:  1. The internal function `_burnFrom` is defined but never called by any public or internal function within `BEP20Zcash`.  2. The `getOwner()` external view function simply calls the inherited `owner()` function from `Ownable`, adding an unnecessary layer of abstraction.  3. The `_msgData()` function in the `Context` library is not used by `BEP20Zcash`, and the `this;` statement within `_msgData()` is a no-op. These elements increase contract size and complexity without providing functionality (7.2 Code Security, 7.1 Architecture).

**Recommendation:** Remove the unused `_burnFrom` function, the redundant `getOwner()` function, and the unused `_msgData()` function along with its `this;` statement. This will reduce contract size, improve readability, and potentially save gas during deployment.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1ba4...8eeb`](https://bscscan.com/address/0x1ba42e5193dfa8b03d15dd1b86a3113bbbef8eeb) |
| **Network** | BNB Chain |
| **Price** | $1,151.0870 |
| **24h Volume** | $2.58M |
| **Liquidity** | $966.6K |
| **Volume / Liquidity** | 2.7× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 84.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6340 buys / 6187 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x4d1b90273d5b0ea98101154d73a6c7d7a19884db)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zcash-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
