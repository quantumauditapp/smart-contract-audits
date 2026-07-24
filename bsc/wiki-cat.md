---
token: WIKI CAT
ticker: WKC
network: bsc
risk_score: 89
status: critical
date: 2026-07-22
---

# WIKI CAT (WKC) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 89/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wiki-cat-bsc)

---

## Audit Summary

The CoinToken contract implements a standard ERC-20 token with added features such as transaction fees, burn fees, pausing functionality, and a blacklist. The contract utilizes an outdated Solidity compiler version and exhibits significant centralization. A critical vulnerability exists where the `burn` function calls an undefined internal function, rendering it non-functional. Additionally, the fee calculation logic is prone to precision errors, and the `updateFee` function is truncated in the provided source.

> **Final Recommendation:** Address the critical `_burn` function implementation error immediately to ensure the burn functionality works as intended. Revise the fee calculation logic to use a standard, precise method (e.g., `value.mul(feeRate).div(100)`) to avoid truncation and ensure accurate fee application. Consider implementing a multi-signature wallet for critical owner-controlled functions to mitigate centralization risks and enhance security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract's technical foundation is based on an outdated Solidity compiler (0.4.24), which introduces potential vulnerabilities and inefficiencies (7.2 Code Security). A critical flaw is present… |
| **Governance / Economics** | 2/10 | High | The contract exhibits a high degree of centralization, with the `owner` possessing extensive control over critical functions (7.3 Access Control, 7.5 Governance). The owner can pause all token… |
| **Upgrades** | 3/10 | High | The provided contract does not implement any proxy or upgradeability patterns (7.7 Upgrades). Therefore, the contract is immutable once deployed, meaning its logic cannot be changed or updated. This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 37.2% |
| **LP Locked** | 99.2% — UNCX |
| **Top-1 Unlocked Holder** | 0.3% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Missing `_burn` Function Implementation  *(Severity: Critical · Status: Unresolved)*

The `CoinToken` contract's `burn` function calls an internal function `_burn(msg.sender, _value);`. However, the `_burn` function is not defined anywhere in the `CoinToken` contract or its inherited contracts (`PausableToken`, `StandardToken`, `ERC20`, `ERC20Basic`, `Pausable`, `Ownable`). This will cause the `burn` function to always revert when called, rendering the token's burn mechanism completely non-functional.

**Recommendation:** Implement the `_burn` function in `CoinToken` or one of its parent contracts, ensuring it correctly reduces `balances[burner]` and `totalSupply`, and emits a `Burn` event. For example, `function _burn(address _burner, uint256 _value) internal { require(_value <= balances[_burner]); balances[_burner] = balances[_burner].sub(_value); totalSupply = totalSupply.sub(_value); emit Burn(_burner, _value); emit Transfer(_burner, address(0), _value); }`


### `H-01` — Inaccurate and Error-Prone Fee Calculation Logic  *(Severity: High · Status: Unresolved)*

The transaction and burn fee calculations use `tempValue.div(uint256(100 / txFee))` and `tempValue.div(uint256(100 / burnFee))`. This approach is problematic because the intermediate division `100 / txFee` (or `100 / burnFee`) performs integer truncation. For example, if `txFee` is 3, `100 / 3` truncates to 33, resulting in a fee of `tempValue / 33` (approx. 3.03%) instead of `tempValue * 3 / 100` (3%). This leads to inaccurate fee collection and unexpected behavior for non-divisor fee percentages. Additionally, if `txFee` or `burnFee` are not positive, the `100 / fee` operation would revert, although a `txFee > 0` check is present.

**Recommendation:** Revise the fee calculation to use a standard and precise method, such as `feeAmount = tempValue.mul(txFee).div(100);` where `txFee` represents the percentage (e.g., 1 for 1%, 5 for 5%). This ensures accurate fee application regardless of the percentage value.


### `H-02` — High Centralization and Extensive Owner Privileges  *(Severity: High · Status: Unresolved)*

The `owner` address holds significant control over the contract's operations. This includes the ability to pause all token transfers, blacklist any address (preventing them from transferring tokens), and unilaterally modify the `txFee`, `burnFee`, and `FeeAddress` through the `updateFee` function. Such extensive centralization introduces a single point of failure and high governance risk, as a compromised owner key could lead to a complete shutdown of token transfers, censorship, or arbitrary fee changes.

**Recommendation:** Consider implementing a multi-signature wallet for the `owner` role to distribute control and reduce the risk associated with a single compromised key. For critical functions like `blackListAddress` or `updateFee`, explore decentralized governance mechanisms or time-locked changes to provide transparency and allow community reaction.


### `M-01` — Outdated Solidity Compiler Version  *(Severity: Medium · Status: Unresolved)*

The contract is compiled with Solidity version `^0.4.24`. This is a significantly outdated compiler version. Newer Solidity versions (e.g., 0.8.x) include important security enhancements, bug fixes, and gas optimizations. For instance, `assert` statements in older versions consume all remaining gas on failure, whereas `require` (and `revert`) refund unused gas, making error handling less efficient. Using an old compiler might expose the contract to known compiler-level vulnerabilities or lead to less efficient code.

**Recommendation:** Upgrade the Solidity compiler version to a recent stable release (e.g., 0.8.x). This will require careful review and testing of the code for breaking changes and potential new warnings, especially regarding integer overflow/underflow checks which are default in 0.8.x.


### `L-01` — Truncated Code in `updateFee` Function  *(Severity: Low · Status: Unresolved)*

The provided source code for the `updateFee` function in `CoinToken` is incomplete, ending abruptly with `FeeAddr...`. This truncation prevents a full security analysis of how the `FeeAddress` is updated and whether proper validation or event emission is included in this critical function.

**Recommendation:** Provide the complete and untruncated source code for all functions to enable a comprehensive security audit. Ensure that the `updateFee` function includes appropriate validation (e.g., `require(_FeeAddress != address(0))`) and emits an event to log the fee changes.


### `I-01` — Misleading Variable Naming for Fees  *(Severity: Informational · Status: Unresolved)*

The variables `txFee` and `burnFee` are named in a way that typically implies a percentage numerator (e.g., `txFee = 5` for 5%). However, their usage in the calculation `tempValue.div(uint256(100 / txFee))` implies they are effectively the denominator of the percentage rate (e.g., if `txFee = 1`, it means 1% because `100/1 = 100`, so `value/100`). This discrepancy between common naming conventions and actual usage can lead to confusion and misconfiguration.

**Recommendation:** Rename `txFee` and `burnFee` to reflect their role as percentage numerators (e.g., `txFeeRate`) and adjust the calculation to `tempValue.mul(txFeeRate).div(100)`. Alternatively, if the current calculation logic is strictly desired, rename the variables to clarify their role as divisors (e.g., `txFeeDivisor`).

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6ec9...8edb`](https://bscscan.com/address/0x6ec90334d89dbdc89e08a133271be3d104128edb) |
| **Network** | BNB Chain |
| **Price** | $0.00000006 |
| **24h Volume** | $45.4K |
| **Liquidity** | $905.9K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 4y |
| **Top-10 Holders** | 43.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 833 buys / 529 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x933477eba23726ca95a957cb85dbb1957267ef85)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wiki-cat-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-22*
