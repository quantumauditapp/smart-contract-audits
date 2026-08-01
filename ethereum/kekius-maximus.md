---
token: Kekius Maximus
ticker: KEKIUS
network: ethereum
risk_score: 24
status: medium
date: 2026-08-01
---

# Kekius Maximus (KEKIUS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 24/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kekius-maximus-eth)

---

## Audit Summary

The Kekius Maximus (KEKIUS) token contract implements a standard ERC-20 interface with additional features for dynamic transaction taxes, anti-bot measures, and automatic liquidity management. The contract utilizes the Ownable pattern, granting significant control to the deployer over critical economic parameters. While some security patterns like reentrancy guards are present, the extensive owner privileges introduce substantial centralization and potential for malicious manipulation, leading to a high overall risk level.

> **Final Recommendation:** It is strongly recommended to significantly decentralize control over critical economic parameters to mitigate the high centralization risk. Consider implementing a multi-signature wallet for sensitive operations or time-locked contracts for parameter changes. Thoroughly review the dynamic tax and anti-bot logic to ensure it cannot be manipulated to create unfair trading conditions or trap user funds. If the intention is for the contract to be immutable, ensure all parameters are set irrevocably at deployment or through a transparent, community-governed process.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract demonstrates a solid foundation with standard ERC-20 implementation and the use of `SafeMath` for arithmetic operations, although `SafeMath` is redundant in Solidity 0.8.23. A reentrancy… |
| **Governance / Economics** | 7/10 | Low | The contract exhibits a high degree of centralization, with the owner possessing extensive control over critical economic parameters (7.4 Economic). The owner can adjust buy/sell taxes, set… |
| **Upgrades** | 9/10 | Low | The contract is not designed to be upgradeable, as it does not implement any proxy patterns (7.7 Upgrades). This eliminates upgrade-related risks but means any discovered vulnerabilities or desired… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 96.5% (≈ permanent lock) |
| **LP Locked** | 96.5% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Honeypot / Rug Pull Potential due to Excessive Owner Control  *(Severity: Critical · Status: Unresolved)*

The contract owner has extensive and unilateral control over critical economic parameters, including `_initialBuyTax`, `_initialSellTax`, `_finalBuyTax`, `_finalSellTax`, `_reduceBuyTaxAt`, `_reduceSellTaxAt`, `_preventSwapBefore`, `_maxTxAmount`, `_maxWalletSize`, `_taxSwapThreshold`, `_maxTaxSwap`, and the `bots` mapping. This allows the owner to set extremely high taxes (up to 21% initially), block transfers for specific addresses, prevent selling for a period (`_preventSwapBefore`), or exclude specific addresses from fees. This combination of controls can be configured to trap user funds, prevent selling for non-owner addresses, or drain liquidity, creating a high risk of a rug pull or…

**Recommendation:** Implement a decentralized governance mechanism (e.g., DAO) or a multi-signature wallet for critical parameter changes. Consider time-locking significant parameter adjustments to provide transparency and allow users to react. Reduce the owner's ability to arbitrarily block transfers or prevent selling. Clearly document the intended behavior of all dynamic parameters and their limits.


### `H-01` — High Centralization of Power  *(Severity: High · Status: Unresolved)*

Numerous critical functions are protected by the `onlyOwner` modifier, granting the deployer address absolute control over the token's economic model and operational flow. This includes the ability to enable/disable trading, set taxes, modify transaction and wallet limits, and manage the `bots` and `_isExcludedFromFee` mappings. This high degree of centralization introduces a single point of failure and a significant trust requirement from users, as the owner can unilaterally make decisions that drastically impact token holders.

**Recommendation:** Explore options to decentralize control over sensitive functions. This could involve implementing a multi-signature wallet for critical operations, introducing a time-lock for parameter changes, or transitioning to a community-governed model where token holders vote on significant protocol adjustments.


### `M-01` — `_preventSwapBefore` Mechanism Can Trap Funds  *(Severity: Medium · Status: Unresolved)*

The `_preventSwapBefore` variable, controlled by the owner, dictates the minimum `_buyCount` before the `swapAndLiquify` function can execute. If set to a high value, this mechanism can effectively prevent the contract from processing accumulated taxes or adding liquidity to the pool for an extended period. This could lead to a build-up of tokens in the contract, delay liquidity provision, and potentially prevent users from selling their tokens if the swap mechanism is crucial for market stability or tax processing.

**Recommendation:** Re-evaluate the necessity and implications of `_preventSwapBefore`. If retained, consider setting a reasonable upper bound for this variable or implementing a time-based lock instead of a `_buyCount` based one. Ensure clear communication to users about this mechanism and its potential impact on trading.


### `M-02` — Anti-Bot/Anti-Whale Mechanisms Bypass Potential  *(Severity: Medium · Status: Unresolved)*

While the `bots` mapping, `_maxTxAmount`, and `_maxWalletSize` are intended to prevent malicious actors and large holders, sophisticated attackers may find ways to bypass these restrictions. For example, using multiple wallets to circumvent wallet size limits or employing complex contract interactions to bypass transaction limits. Furthermore, the owner's ability to add/remove bots and exclude addresses from fees can be misused to selectively apply these restrictions, creating an unfair playing field.

**Recommendation:** Acknowledge that anti-bot/anti-whale measures are often imperfect and can be bypassed. Focus on making the token's core economics robust rather than relying solely on these mechanisms. If retained, ensure the owner's control over these features is transparent and subject to checks, such as time-locks or multi-signature approvals.


### `M-03` — `renounceOwnership` Implications for Dynamic Tokenomics  *(Severity: Medium · Status: Unresolved)*

The `renounceOwnership` function is present, allowing the owner to transfer ownership to the zero address. However, given the contract's highly dynamic tax system, anti-bot measures, and liquidity management, renouncing ownership would render many critical functions inaccessible. This would effectively 'brick' the contract's ability to adapt to market conditions, adjust taxes, or manage liquidity, potentially leading to an unmanageable or broken state for the token.

**Recommendation:** If the intention is for the contract to be immutable after deployment, ensure all dynamic parameters are set to their final, desired values before renouncing ownership. Alternatively, remove the `renounceOwnership` function if continuous owner intervention is expected for the token's operation. If renouncing ownership is desired, consider a phased approach or a transfer of ownership to a community-controlled multi-sig or DAO.


### `L-01` — Hardcoded Tax Wallet in Constructor  *(Severity: Low · Status: Unresolved)*

The `_taxWallet` address is hardcoded in the constructor (`_taxWallet = payable(0xa86DA6b1b09795BB2bcEe46D65b4d295Faaf002B);`). While there is a `setTaxWallet` function to change it later, an incorrect or compromised address initially hardcoded could lead to misdirection of funds before the `setTaxWallet` function is called.

**Recommendation:** Consider passing the `_taxWallet` address as a constructor argument to ensure it is explicitly set at deployment. This reduces the risk of an incorrect hardcoded value and improves deployment flexibility.


### `I-01` — Unnecessary SafeMath Library Usage  *(Severity: Informational · Status: Unresolved)*

The contract uses the `SafeMath` library for arithmetic operations (e.g., `add`, `sub`, `mul`, `div`). However, the contract is compiled with Solidity version 0.8.23, which natively includes checked arithmetic, meaning integer overflow and underflow will automatically revert. Therefore, the `SafeMath` library is redundant and adds unnecessary bytecode and gas cost without providing additional security benefits in this Solidity version.

**Recommendation:** Remove the `SafeMath` library and its usage. Rely on Solidity's native checked arithmetic for `uint256` operations. This will reduce contract size and slightly optimize gas costs.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x26e5...7dd9`](https://etherscan.io/address/0x26e550ac11b26f78a04489d5f20f24e3559f7dd9) |
| **Network** | Ethereum |
| **Price** | $0.004489 |
| **24h Volume** | $401.1K |
| **Liquidity** | $645.2K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 47.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 517 buys / 690 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xfff8d5fff6ee3226fa2f5d7d5d8c3ff785be9c74)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kekius-maximus-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-01*
