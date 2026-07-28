---
token: Request Token
ticker: REQ
network: ethereum
risk_score: 40
status: medium
date: 2026-07-26
---

# Request Token (REQ) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/request-token-eth)

---

## Audit Summary

This audit covers the provided Solidity source code for an ERC-20 token (`StandardToken`) and a partial crowdsale contract (`StandardCrowdsale`). The token contract utilizes `SafeMath` for arithmetic operations, enhancing security against integer overflows/underflows. However, the standard ERC-20 `approve` function is susceptible to a known race condition. The crowdsale contract is incomplete, limiting a full assessment. The project uses an outdated Solidity compiler version (0.4.15).

> **Final Recommendation:** It is strongly recommended to upgrade the Solidity compiler version to a more recent and supported release (e.g., 0.8.x) to benefit from modern security features and optimizations. Address the ERC-20 `approve` race condition by advising users to utilize `increaseApproval` and `decreaseApproval` functions, or by implementing a two-step approval process (setting allowance to zero before increasing). Finally, a complete review of the `StandardCrowdsale` contract is essential once the full source code is available, focusing on its token creation, fund management, and any potential refund mechanisms.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | 7.1 Architecture: The architecture follows standard ERC-20 and Crowdsale patterns, utilizing `Ownable` for access control and `SafeMath` for robust arithmetic operations. 7.2 Code Security… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic: The primary economic risk identified is the ERC-20 `approve` race condition (M-01), which could lead to unintended token transfers if not handled carefully by users. The crowdsale's… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The provided contracts do not implement any upgradeability patterns (e.g., proxies). This means the contracts are immutable once deployed, eliminating upgrade-specific risks but also… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — ERC-20 `approve()` Race Condition Vulnerability  *(Severity: Medium · Status: Unresolved)*

The `approve` function in the `StandardToken` contract is susceptible to a known ERC-20 race condition. If a token holder increases an allowance for a spender, and the spender has a pending transaction to spend the old allowance, the spender might be able to spend both the old and new allowances, leading to an unintended total amount spent. While the contract includes `increaseApproval` and `decreaseApproval` as mitigation, the `approve` function itself remains vulnerable.

**Recommendation:** Advise users to exclusively use `increaseApproval` and `decreaseApproval` functions instead of `approve` when modifying existing allowances. Alternatively, implement a two-step approval process where the allowance is first set to zero before being updated to a new value, or ensure that the `approve` function checks if `_value` is non-zero when `allowed[msg.sender][_spender]` is also non-zero.


### `L-01` — Outdated Solidity Compiler Version  *(Severity: Low · Status: Unresolved)*

The contract is compiled with Solidity version 0.4.15. This version is significantly outdated and no longer actively maintained. Newer compiler versions (e.g., 0.8.x) include critical bug fixes, security enhancements, and improved code generation that can prevent various vulnerabilities and optimize gas usage. While `SafeMath` mitigates common integer issues, other compiler-specific risks might exist.

**Recommendation:** Upgrade the Solidity compiler version to a recent and actively supported release (e.g., 0.8.x). This will require careful review and testing of the code for compatibility and potential breaking changes, especially regarding `require`/`assert`/`revert` behavior and integer overflow checks.


### `I-01` — Incomplete Crowdsale Contract Provided  *(Severity: Informational · Status: Unresolved)*

The provided source code for the `StandardCrowdsale` contract is truncated. Critical functions and logic related to token creation (`createTokenContract`), token distribution, fund management, capping, and potential refund mechanisms are missing. This prevents a comprehensive security assessment of the crowdsale's full functionality and potential vulnerabilities.

**Recommendation:** Provide the complete and unabridged source code for the `StandardCrowdsale` contract to enable a full and accurate security audit. This is essential for identifying any hidden vulnerabilities or design flaws.


### `I-02` — Crowdsale Start Time Front-Running Potential  *(Severity: Informational · Status: Unresolved)*

The `StandardCrowdsale` constructor includes a check `require(_startTime >= now)`. While this ensures the crowdsale doesn't start in the past, if `_startTime` is set to be very close to the deployment time, a malicious actor could potentially front-run the deployment transaction to deploy their own contract slightly earlier, or manipulate the `block.timestamp` if the miner colludes, though the latter is less likely for simple `now` checks.

**Recommendation:** Consider adding a small grace period between `_startTime` and the expected deployment time, or ensure `_startTime` is sufficiently in the future to prevent any minor front-running attempts. For critical time-sensitive operations, consider using an oracle or a multi-transaction setup to initiate the crowdsale.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8f82...938a`](https://etherscan.io/address/0x8f8221afbb33998d8584a2b05749ba73c37a938a) |
| **Network** | Ethereum |
| **Price** | $0.0512 |
| **24h Volume** | $16.7K |
| **Liquidity** | $128.0K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 5y |
| **Top-10 Holders** | 42.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 290 buys / 547 sells |

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

## Frequently Asked Questions

### Is Request Token a scam?

Based on automated analysis, Request Token scores 33/100 (Medium Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Request Token safe to buy?

Our scanner flagged a risk score of 33/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Request Token been audited?

The contract is open-source and verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x5522c339d35a6c3e5f328c8746bdf88f599dab83)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/request-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-26*
