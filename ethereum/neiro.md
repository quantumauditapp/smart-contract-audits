---
token: Neiro
ticker: NEIRO
network: ethereum
risk_score: 42
status: medium
date: 2026-08-11
---

# Neiro (NEIRO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/neiro-eth)

---

## Audit Summary

The Neiro token contract implements standard ERC-20 functionality with custom tokenomics including dynamic taxes, anti-whale mechanisms, and Uniswap integration. While it utilizes SafeMath and a reentrancy guard for swaps, the audit identified a critical risk related to unlocked liquidity, alongside high risks concerning immutable economic parameters and an unchangeable tax wallet. Several medium and low-level issues also exist, primarily impacting access control and economic flexibility.

> **Final Recommendation:** Address the critical vulnerability of the unlocked liquidity pool immediately by locking LP tokens with a reputable service for a substantial duration. Implement `onlyOwner` functions to allow for the adjustment of critical economic parameters (e.g., tax rates, transaction limits) and the `_taxWallet` address, ensuring operational flexibility and security. Thoroughly review and simplify the complex tax calculation logic to reduce the risk of unintended behavior or manipulation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates good practices by using SafeMath for arithmetic operations and implementing a reentrancy guard (`lockTheSwap`) for external calls to Uniswap (7.2 Code Security). However… |
| **Governance / Economics** | 3/10 | High | The economic model features dynamic buy/sell taxes and anti-whale limits, which are intended to manage token distribution and price stability (7.4 Economic). However, the prefill indicates the… |
| **Upgrades** | 8/10 | Low | The Neiro contract is not designed as an upgradeable proxy (7.7 Upgrades). This means its code is immutable once deployed, eliminating risks associated with upgrade mechanisms like proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Unlocked Liquidity Pool (Rug Pull Risk)  *(Severity: Critical · Status: Unresolved)*

The provided prefill data indicates that the liquidity pool (LP) for the Neiro token is currently unlocked. This allows the deployer or owner of the LP tokens to remove all or a significant portion of the liquidity at any time, leading to a 'rug pull' scenario where token holders are unable to sell their tokens, resulting in a complete loss of value. This is a critical trust and security issue for investors. (7.6 External, 7.4 Economic)

**Recommendation:** Immediately lock the liquidity pool tokens with a reputable, audited locker service for a significant duration (e.g., 1-5 years or permanently). Provide verifiable proof of the LP lock to the community to build trust and mitigate this critical risk.


### `H-01` — Immutable Critical Economic Parameters  *(Severity: High · Status: Unresolved)*

Key economic parameters such as `_initialBuyTax`, `_initialSellTax`, `_finalBuyTax`, `_finalSellTax`, `_reduceBuyTaxAt`, `_reduceSellTaxAt`, `_maxTxAmount`, `_maxWalletSize`, `_taxSwapThreshold`, and `_maxTaxSwap` are hardcoded in the contract and lack owner-controlled setter functions. This design choice prevents any adjustment to the token's economic model, making it inflexible to market changes, necessary rebalancing, or correction of misconfigurations. (7.3 Access Control, 7.4 Economic)

**Recommendation:** Implement `onlyOwner` functions to allow the contract owner to adjust these critical economic parameters within predefined, reasonable bounds. This provides necessary flexibility for protocol management while maintaining security. Consider a timelock for sensitive parameter changes.


### `H-02` — Unchangeable Tax Wallet Address  *(Severity: High · Status: Unresolved)*

The `_taxWallet` address, which receives all collected transaction taxes, is set to the deployer's address in the constructor and cannot be changed post-deployment. If this address is compromised, lost, or needs to be updated for operational reasons (e.g., migration to a multi-signature wallet), all collected taxes will be sent to an unrecoverable or incorrect address, leading to a loss of funds. (7.3 Access Control, 7.8 Operations)

**Recommendation:** Implement an `onlyOwner` function to allow the contract owner to update the `_taxWallet` address. It is highly recommended to use a multi-signature wallet or a timelock-controlled address for the tax wallet to enhance security and decentralization.


### `M-01` — Complex and Potentially Manipulable Dynamic Tax Mechanism  *(Severity: Medium · Status: Unresolved)*

The token's tax mechanism is complex, featuring dynamic buy and sell taxes that change based on global transaction counters (`_buyCount`, `sellCount`) and predefined thresholds (`_reduceBuyTaxAt`, `_reduceSellTaxAt`). This complexity increases the risk of unexpected behavior, miscalculation, or potential manipulation by large buyers/sellers who could strategically time transactions to influence tax tiers for others. (7.4 Economic, 7.2 Code Security)

**Recommendation:** Thoroughly test the dynamic tax mechanism under various simulated market conditions and transaction patterns to identify and mitigate potential exploits or unintended consequences. Consider simplifying the tax structure or making the thresholds more robust against manipulation to ensure fairness and predictability.


### `M-02` — Permanent Exile List  *(Severity: Medium · Status: Unresolved)*

The `isExile` mapping, used to exempt specific addresses (owner, contract, Uniswap pair) from taxes and transaction limits, is initialized only in the constructor. There are no functions to add or remove addresses from this list post-deployment. This lack of flexibility could hinder future operational needs, such as exempting new exchange addresses or removing compromised/malicious addresses from the exemption list. (7.3 Access Control)

**Recommendation:** Implement `onlyOwner` functions to allow the contract owner to add and remove addresses from the `isExile` list. This provides necessary administrative control to manage exemptions dynamically as the project evolves.


### `L-01` — Impact of Renouncing Ownership  *(Severity: Low · Status: Unresolved)*

The `renounceOwnership` function is available, allowing the owner to transfer ownership to the zero address. If ownership is renounced, the contract becomes immutable in terms of administrative control. This means all `onlyOwner` functions, including `setMarketPair` and any future functions intended for parameter adjustments, would become permanently inaccessible. (7.3 Access Control, 7.5 Governance)

**Recommendation:** Ensure a clear understanding of the implications before renouncing ownership. If immutability of administrative control is the desired long-term state, confirm that all necessary parameters are correctly configured and no future administrative actions will be required. Otherwise, consider not renouncing ownership or transferring it to a secure, multi-signature wallet.


### `I-01` — First Block Buy Limit  *(Severity: Informational · Status: Unresolved)*

The contract implements a specific mechanism to limit the number of buy transactions on the very first block (`block.number == firstBlock`) to 51 per block (`perBuyCount[block.number] < 51`). This is likely intended as an anti-bot or anti-whale measure during the initial launch phase. While a design choice, it could limit legitimate early participation or create a competitive environment for initial buys. (7.4 Economic)

**Recommendation:** Clearly document this specific behavior for potential users and investors to manage expectations during the token launch. Ensure this mechanism aligns with the project's overall launch strategy and desired initial distribution.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x812b...53ee`](https://etherscan.io/address/0x812ba41e071c7b7fa4ebcfb62df5f45f6fa853ee) |
| **Network** | Ethereum |
| **Price** | $0.0000683 |
| **24h Volume** | $291.5K |
| **Liquidity** | $2.68M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2y |
| **Top-10 Holders** | 73.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 218 buys / 365 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xc555d55279023e732ccd32d812114caf5838fd46)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/neiro-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
