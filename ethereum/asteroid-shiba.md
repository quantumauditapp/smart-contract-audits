---
token: Asteroid Shiba
ticker: ASTEROID
network: ethereum
risk_score: 18
status: low
date: 2026-06-19
---

# Asteroid Shiba (ASTEROID) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 18/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/asteroid-shiba-eth)

---

## Audit Summary

The Asteroid Shiba (AS) token contract is an ERC-20 token with significant owner privileges, including the ability to modify tax rates, transaction limits, and wallet size limits. This high degree of centralization introduces critical risks, including the potential for a honeypot scenario where the owner could prevent users from selling or impose prohibitive taxes. While the contract implements anti-bot and anti-whale measures, these can be bypassed by the owner. The use of SafeMath is redundant in Solidity 0.8.25, and a lack of event emissions for critical state changes reduces transparency.

> **Final Recommendation:** Given the critical centralization risks and potential for a honeypot, users should exercise extreme caution. It is strongly recommended to decentralize control over critical parameters by implementing a multi-signature wallet or a time-locked governance mechanism for sensitive functions. All critical state changes should emit events to ensure transparency and allow for off-chain monitoring. Consider removing the redundant SafeMath library to optimize gas usage. Thoroughly review and test all anti-bot and anti-whale mechanisms to ensure they function as intended and cannot be easily bypassed, especially by the owner.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract's technical architecture (7.1) is a standard ERC-20 implementation with added tax and anti-bot/anti-whale mechanisms. Code security (7.2) benefits from Solidity 0.8.25's built-in… |
| **Governance / Economics** | 7/10 | Low | The economic model (7.4) is highly centralized, granting the owner extensive control over all critical parameters, including buy/sell taxes, transaction limits, wallet size limits, and the ability to… |
| **Upgrades** | 8/10 | Low | The contract is not designed to be upgradeable (7.7). There are no proxy patterns or upgrade interfaces implemented, meaning the contract's logic is immutable once deployed. This eliminates… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 95.9% (≈ permanent lock) |
| **LP Locked** | 95.9% — Null Address |

## Security Findings

_🔴 2 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `C-01` — Extreme Centralization and Owner Privileges  *(Severity: Critical · Status: Unresolved)*

The contract owner possesses extensive control over nearly all critical parameters, including tax rates (_initialBuyTax, _initialSellTax, _finalBuyTax, _finalSellTax), transaction limits (_maxTxAmount), wallet size limits (_maxWalletSize), swap thresholds (_taxSwapThreshold, _maxTaxSwap), anti-bot measures (sellsPerBlock, buysFirstBlock), and the ability to enable/disable trading (tradingOpen, swapEnabled). The owner can also whitelist addresses via the `isExile` mapping to bypass all restrictions. This level of centralization allows the owner to unilaterally alter the token's economic model and operational behavior, posing a severe risk to token holders.

**Recommendation:** Decentralize control over critical parameters. Implement a multi-signature wallet for sensitive operations or introduce a time-locked governance mechanism for changes to tax rates, limits, and trading status. Remove the `isExile` mapping or restrict its use to only essential protocol addresses, not arbitrary user addresses.


### `C-02` — Honeypot Potential  *(Severity: Critical · Status: Unresolved)*

Due to the extreme centralization (C-01), the contract has significant honeypot potential. The owner can, at any time, set the sell tax to 100%, set the maximum transaction amount for sells to zero, or set the maximum wallet size to a value that prevents existing holders from selling. This would effectively trap user funds within the contract, making them unsellable and leading to total loss for investors.

**Recommendation:** Implement immutable tax rates and transaction limits, or subject any changes to a decentralized governance process with a time-lock. Ensure that minimum sell transaction amounts and maximum wallet sizes cannot be set to values that would prevent legitimate users from selling their tokens.


### `H-01` — Anti-Bot/Anti-Whale Mechanisms Bypass  *(Severity: High · Status: Unresolved)*

The contract implements anti-bot (e.g., `sellsPerBlock`, `buysFirstBlock`) and anti-whale (`_maxTxAmount`, `_maxWalletSize`) mechanisms. However, the `isExile` mapping, controlled by the owner, allows any address to bypass these restrictions. This means the owner can whitelist their own addresses or those of favored parties, rendering the anti-bot/anti-whale measures ineffective for those addresses and creating an unfair advantage or potential for manipulation.

**Recommendation:** Re-evaluate the necessity and scope of the `isExile` mapping. If critical for protocol operations, restrict its use to only contract-internal addresses (e.g., router, treasury) and remove the owner's ability to add arbitrary user addresses. Ensure all users are subject to the same rules.


### `M-01` — Lack of Event Emission for Critical State Changes  *(Severity: Medium · Status: Unresolved)*

Many critical owner-controlled parameters, such as `_maxTxAmount`, `_maxWalletSize`, various tax rates, `swapEnabled`, `tradingOpen`, `sellsPerBlock`, `buysFirstBlock`, and `isExile` status, can be modified without emitting corresponding events. This lack of transparency makes it difficult for users and off-chain monitoring tools to track changes to the contract's behavior and economic model, increasing trust requirements.

**Recommendation:** Emit explicit events for every function that modifies a critical state variable. For example, `MaxTxAmountUpdated(uint256 newAmount)`, `TaxRatesUpdated(uint256 newBuyTax, uint256 newSellTax)`, `SwapEnabledToggled(bool status)`, `ExileStatusUpdated(address indexed account, bool isExiled)`. This improves transparency and auditability.


### `M-02` — Potential for Stuck ETH in Swap Mechanism  *(Severity: Medium · Status: Unresolved)*

The `swapAndLiquify` function transfers ETH to the `_taxWallet` after swapping tokens. If the `_taxWallet` address is a contract that does not have a `receive()` or `fallback()` function capable of accepting ETH, or if it reverts during the transfer, the entire swap operation could fail. This could lead to a denial of service for the automatic liquidity/tax collection mechanism, potentially accumulating tokens in the contract without being able to process them.

**Recommendation:** Implement robust error handling for external ETH transfers. Consider adding a mechanism for the owner to recover stuck ETH from the contract if the `_taxWallet` becomes problematic. Ensure the `_taxWallet` is a reliable address or a contract designed to accept ETH.


### `L-01` — Unchecked Return Values for External Calls  *(Severity: Low · Status: Unresolved)*

The contract makes external calls to `IUniswapV2Factory.createPair` and `IUniswapV2Router02.swapExactTokensForETHSupportingFeeOnTransferTokens` without explicitly checking their boolean return values. While Uniswap functions typically revert on failure, explicitly checking return values is a best practice to ensure expected behavior and prevent unexpected state. The `_approve` function is internal, but its usage in `transferFrom` relies on `SafeMath` for allowance checks.

**Recommendation:** Explicitly check the return values of external calls where applicable, especially for functions that return a boolean indicating success or failure. Although Uniswap functions often revert, defensive programming suggests checking for unexpected behavior.


### `I-01` — Redundant SafeMath Library  *(Severity: Informational · Status: Unresolved)*

The contract uses the `SafeMath` library for arithmetic operations. However, the contract is compiled with Solidity 0.8.25, which includes built-in overflow and underflow checks by default. The use of `SafeMath` in this context is redundant and adds unnecessary gas overhead for each arithmetic operation.

**Recommendation:** Remove the `SafeMath` library and directly use native arithmetic operators. Solidity 0.8.0 and later versions automatically handle overflow/underflow, making `SafeMath` obsolete for basic arithmetic.


### `I-02` — Hardcoded Uniswap Router Address  *(Severity: Informational · Status: Unresolved)*

The Uniswap V2 Router address (0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D) is hardcoded in the constructor. While this is common for mainnet deployments, it reduces flexibility. If the Uniswap router address changes in the future or if the contract were to be deployed on a different network with a different router address, the contract would need to be redeployed.

**Recommendation:** Consider making the Uniswap router address configurable by the owner through a setter function, or pass it as a constructor argument. This would allow for greater flexibility and adaptability to future changes or multi-chain deployments.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf280...4126`](https://etherscan.io/address/0xf280b16ef293d8e534e370794ef26bf312694126) |
| **Network** | Ethereum |
| **Price** | $0.0001635 |
| **24h Volume** | $18.72M |
| **Liquidity** | $2.55M |
| **Volume / Liquidity** | 7.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 13.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5742 buys / 4731 sells |

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

## Frequently Asked Questions

### Is Asteroid Shiba a scam?

Based on available on-chain data, Asteroid Shiba exhibits characteristics that typically differentiate it from common scam projects. The contract is verified, ownership has been renounced, and no mint function exists, which collectively reduce the risk of rug pulls or unauthorized token creation by the deployer. These factors suggest a degree of technical robustness and transparency.

### Is Asteroid Shiba safe to buy?

Asteroid Shiba features several safety measures, including locked liquidity and renounced ownership, which contribute to its low-risk score of 0/100 from a contract security standpoint. However, no cryptocurrency investment is entirely without risk. Investors should be aware of the 13.7% token concentration among the top 10 holders and the inherent volatility of the crypto market.

### Has Asteroid Shiba been audited?

The provided data indicates the Asteroid Shiba contract is 'verified,' meaning its source code is publicly available and matches the deployed bytecode on the Ethereum blockchain. While this promotes transparency, it is distinct from a formal security audit conducted by an independent third party, which would typically involve a deeper code review for vulnerabilities.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x76a411f14a704099ba476ce8dffc288a53295218)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/asteroid-shiba-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-19*
