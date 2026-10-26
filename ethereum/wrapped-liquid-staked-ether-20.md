---
token: Wrapped liquid staked Ether 2.0
ticker: WSTETH
network: ethereum
risk_score: 1
status: low
date: 2026-08-11
---

# Wrapped liquid staked Ether 2.0 (WSTETH) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-liquid-staked-ether-20-eth)

---

## Audit Summary

The audited contract is a standard ERC20 token implementation, likely based on OpenZeppelin's well-vetted libraries. It utilizes SafeMath for arithmetic safety and adheres to common security practices. The primary findings are informational, related to the base contract's non-functional state without further implementation (e.g., initial supply minting) and the presence of the ECDSA library without a corresponding permit function. One low-severity finding notes the potential for misuse of the `_beforeTokenTransfer` hook if overridden by a derived contract. Overall, the technical risk is low, reflecting a robust and secure foundation.

> **Final Recommendation:** The provided ERC20 contract serves as a robust and well-audited base for a token implementation. For the `WstETH` token, it is crucial to ensure that the inheriting contract properly initializes the token's total supply and implements any necessary minting or burning mechanisms with appropriate access controls. Additionally, if the `permit` functionality is intended, its implementation should be carefully reviewed. Consider using a more recent Solidity compiler version for future deployments to leverage native safety features.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture is based on a well-established OpenZeppelin ERC20 standard, leveraging `SafeMath` for robust arithmetic operations (7.1 Architecture, 7.2 Code Security). The contract… |
| **Governance / Economics** | 10/10 | Low | The contract implements standard ERC20 token economics, focusing on transfers and allowances without complex economic models or governance mechanisms (7.4 Economic, 7.5 Governance). The base contract… |
| **Upgrades** | 10/10 | Low | The contract is not designed with an upgradeability pattern (e.g., proxy) (7.7 Upgrades). This simplifies the deployment model by eliminating upgrade-related risks such as storage collisions or logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 56.4% |
| **Top-3 Unlocked** | 78.6% |

## Security Findings

_🟢 1 Low · ⚪ 7 Informational_

### `L-01` — Potential for Misuse of `_beforeTokenTransfer` Hook  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_beforeTokenTransfer` hook is an `internal virtual` function that is called before any token transfer, mint, or burn operation. While it is empty in the base `ERC20` contract, a derived contract could override this function to introduce complex logic, reentrancy vectors, or other vulnerabilities if not implemented carefully. Improperly implemented custom logic in this hook could lead to unexpected behavior or security exploits.

**Recommendation:** Any contract inheriting from `ERC20` and overriding `_beforeTokenTransfer` must ensure that the custom logic is thoroughly audited for reentrancy, gas limits, and other potential side effects. Avoid external calls within this hook or ensure they are protected against reentrancy if necessary.


### `I-01` — Token Non-Functional As-Is  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ERC20` contract, as provided, initializes `_totalSupply` to 0 and does not expose any public or external functions for minting new tokens. This means that upon deployment, the token will have a total supply of zero, rendering it non-functional for transfers unless a derived contract implements minting logic (e.g., in its constructor or via an external function). This is a design choice for a base contract but makes it unusable as a standalone token.

**Recommendation:** Ensure that the inheriting contract (e.g., `WstETH`) properly implements initial token supply minting or provides controlled minting mechanisms to make the token functional. This typically involves calling the internal `_mint` function in the constructor of the derived token contract or through an externally callable function with appropriate access control.


### `I-02` — `ECDSA` Library Present but `permit` Not Implemented  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ECDSA` library and `IERC20Permit` interface are included in the codebase, suggesting an intention to implement the ERC-2612 `permit` functionality. However, the `ERC20` contract itself does not implement the `permit` function, which allows users to approve token transfers via a signed message rather than an on-chain transaction.

**Recommendation:** If `permit` functionality is desired for the `WstETH` token, ensure it is correctly implemented in the derived contract, leveraging the `ECDSA` library for signature verification and adhering to the ERC-2612 standard. Pay close attention to nonce management and signature validation to prevent replay attacks.


### `I-03` — Use of Older Solidity Version  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses Solidity version `0.6.12`. While this version is generally stable and widely used, newer versions (e.g., `0.8.x`) include built-in overflow/underflow checks, removing the explicit need for `SafeMath` and potentially simplifying the code. Newer compilers also offer various optimizations and bug fixes.

**Recommendation:** Consider upgrading to Solidity `0.8.x` or later for new deployments to benefit from native overflow checks and other compiler improvements. If upgrading, ensure all code is compatible with the new compiler version and thoroughly re-audited, as syntax and behavior changes may exist.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 65.4% of supply. What remains: 1.1% in wallets, 64.4% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Wrapped stETH (WSTETH), market cap $10.7B. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18.6M (DexScreener, all pools). 24h trading volume $2.6M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Liquid staking token  *(Severity: Informational · Status: Acknowledged)*

A receipt for staked native tokens that keeps earning staking rewards. Its value depends on the staking protocol and its validators. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Liquid Staking Tokens. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18.6M of DEX liquidity across 19 pools. Launch: 1450 days of market history.

**Recommendation:** Check the staking protocol's validator set, withdrawal queue and governance.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7f39...2ca0`](https://etherscan.io/address/0x7f39c581f595b53c5cb19bd0b3f8da6c935e2ca0) |
| **Network** | Ethereum |
| **Price** | $3,129.5300 |
| **24h Volume** | $2.65M |
| **Liquidity** | $6.42M |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 4y |
| **Top-10 Holders** | 65.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 138 buys / 83 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x109830a1aaad605bbf02a9dfa7b0b92ec2fb7daa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-liquid-staked-ether-20-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
