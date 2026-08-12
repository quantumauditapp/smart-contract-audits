---
token: Aliens
ticker: ALIENS
network: ethereum
risk_score: 25
status: medium
date: 2026-08-12
---

# Aliens (ALIENS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 25/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aliens-eth)

---

## Audit Summary

The ALIENS token contract implements standard ERC-20 functionality alongside complex anti-whale, anti-bot, and tax mechanisms. While `SafeMath` is used to prevent integer overflows/underflows, the contract exhibits significant centralization risks due to extensive owner control over critical parameters, including taxes, transaction limits, and trading status. A reentrancy vulnerability in the ETH transfer mechanism and the use of `tx.origin` for transfer delays are also identified. These issues collectively pose a high risk of economic manipulation and potential for a rug pull.

> **Final Recommendation:** It is strongly recommended to decentralize control over critical contract parameters where possible, or to implement a multi-signature wallet for administrative functions to mitigate single points of failure and reduce rug pull potential. The identified reentrancy vulnerability in `sendETHToFee` should be addressed by implementing a Checks-Effects-Interactions pattern or using a reentrancy guard. The use of `tx.origin` should be replaced with `msg.sender` for security best practices.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes `SafeMath` for arithmetic operations, mitigating common integer overflow/underflow vulnerabilities (7.2 Code Security). A `lockTheSwap` modifier is used to prevent reentrancy… |
| **Governance / Economics** | 7/10 | Low | The contract grants the owner extensive control over all critical economic parameters, including initial and final buy/sell taxes, tax reduction thresholds, maximum transaction amounts, maximum… |
| **Upgrades** | 9/10 | Low | The contract is not designed with upgradeability patterns (e.g., proxy contracts). Therefore, there are no upgrade-specific risks (7.7 Upgrades). Any changes to the contract's logic would require… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Centralized Control and Potential for Rug Pull  *(Severity: Critical · Status: Unresolved)*

The contract owner possesses extensive control over critical economic parameters and operational flags. This includes the ability to set initial/final buy/sell taxes, transaction limits (`_maxTxAmount`, `_maxWalletSize`), enable/disable trading (`tradingOpen`), enable/disable swaps (`swapEnabled`), and manage a `bots` list. The `removeLimits` function allows the owner to completely disable transaction and wallet size restrictions. This level of centralized control enables the owner to manipulate the token's economy, potentially leading to a rug pull by removing liquidity, disabling taxes for themselves, and dumping tokens without restrictions. (7.3 Access Control, 7.4 Economic, 7.5 Governan…

**Recommendation:** Implement a time-locked multi-signature wallet for critical administrative functions to introduce a delay and require consensus for changes. Consider decentralizing control over some parameters or hardcoding certain values to prevent arbitrary changes. If `removeLimits` is intended for a specific post-launch phase, ensure clear communication and consider a time-locked mechanism for its activation.


### `H-01` — Reentrancy Vulnerability in `sendETHToFee`  *(Severity: High · Status: Unresolved)*

The `sendETHToFee` function performs a direct ETH transfer to `_taxWallet` using `call` after a token swap, but before the `inSwap` reentrancy lock is released. If `_taxWallet` is a malicious contract, it could reenter the `_transfer` function (or other functions that interact with the contract's ETH balance) while `inSwap` is still true, potentially draining the contract's ETH balance before it's fully distributed or accounted for. (7.2 Code Security)

**Recommendation:** Apply the Checks-Effects-Interactions pattern. Ensure that the `inSwap` flag is reset immediately after the external call to `swapTokensForEth` and before `sendETHToFee` is called, or implement a reentrancy guard specifically for `sendETHToFee` if it's called independently. Alternatively, ensure `_taxWallet` is an EOA or a trusted contract that does not reenter.


### `H-02` — `tx.origin` Usage for Transfer Delay  *(Severity: High · Status: Unresolved)*

The `_holderLastTransferTimestamp` check within the `_transfer` function uses `tx.origin` to enforce a transfer delay (one purchase per block). While this might be intended to prevent contract-based bots, `tx.origin` is generally discouraged in security-sensitive contexts due to its susceptibility to phishing attacks. A malicious contract could trick a user into calling it, and then that contract could call `_transfer` on behalf of the user, potentially bypassing `msg.sender`-based checks if they were present elsewhere, or leading to unexpected behavior. (7.2 Code Security)

**Recommendation:** Replace `tx.origin` with `msg.sender` for all access control and state-modifying checks. If the intent is specifically to prevent contract interactions, consider alternative mechanisms that do not rely on `tx.origin`.


### `M-01` — High Initial Taxes and Dynamic Tax Changes  *(Severity: Medium · Status: Unresolved)*

The contract sets initial buy and sell taxes at 25%, which is exceptionally high and can significantly deter legitimate trading activity and liquidity provision. Furthermore, the owner has the ability to dynamically adjust these tax rates (`_initialBuyTax`, `_finalBuyTax`, `_initialSellTax`, `_finalSellTax`), tax reduction thresholds (`_reduceBuyTaxAt`, `_reduceSellTaxAt`), and swap parameters (`_preventSwapBefore`, `_taxSwapThreshold`, `_maxTaxSwap`). This high degree of flexibility introduces significant economic uncertainty and potential for abuse, as the owner could change taxes at any time to their advantage. (7.4 Economic)

**Recommendation:** Consider reducing initial tax rates to a more sustainable level to encourage trading. If dynamic tax changes are necessary, implement a timelock or a community governance mechanism to provide transparency and prevent sudden, arbitrary changes. Clearly communicate the tax structure and any potential changes to the community.


### `M-02` — Anti-Bot/Anti-Whale Mechanisms Can Be Abused  *(Severity: Medium · Status: Unresolved)*

The contract includes robust anti-bot and anti-whale features such as `_maxTxAmount`, `_maxWalletSize`, `transferDelayEnabled`, and a `bots` mapping. While these are intended to prevent manipulation, the owner's absolute control over these parameters allows for potential abuse. The owner can selectively exclude users, disable limits for specific addresses, or use these features to create a 'honeypot' scenario where limits are enforced during initial buys but removed later to facilitate a large dump. (7.3 Access Control, 7.4 Economic)

**Recommendation:** Ensure transparent communication regarding the use and purpose of these anti-manipulation features. Consider implementing a community-driven or time-locked mechanism for changes to these parameters to prevent arbitrary abuse. Clearly define the criteria for adding/removing addresses from the `bots` list.


### `L-01` — Redundant `min` Function Definition  *(Severity: Low · Status: Unresolved)*

The contract defines the `min` function twice, once taking `uint256` arguments and once taking `uint` arguments. Since `uint` is an alias for `uint256` in Solidity, these definitions are functionally identical and redundant. (7.2 Code Security)

**Recommendation:** Remove one of the `min` function definitions, as `uint` and `uint256` are the same type. This will improve code clarity and reduce unnecessary duplication.


### `I-01` — Lack of Event Emission for Critical State Changes  *(Severity: Informational · Status: Unresolved)*

Several critical state changes, such as modifications to tax rates, transaction limits, `tradingOpen`, `swapEnabled`, `transferDelayEnabled`, `_preventSwapBefore`, `_taxSwapThreshold`, `_maxTaxSwap`, `_taxWallet`, and the `bots` mapping, do not emit corresponding events. This lack of event emission makes it difficult for off-chain monitoring tools, block explorers, and users to track important administrative actions and changes to the contract's operational parameters. (7.8 Operations)

**Recommendation:** Emit events for all critical state changes, especially those controlled by the owner. This enhances transparency, auditability, and allows for better monitoring of the contract's lifecycle and administrative actions.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc778...0fdc`](https://etherscan.io/address/0xc77867d630dbe567d219a86fddbe7ef1f0670fdc) |
| **Network** | Ethereum |
| **Price** | $0.000019 |
| **24h Volume** | $83.5K |
| **Liquidity** | $51.7K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 2y |
| **Top-10 Holders** | 33.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 167 buys / 104 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x0a4bcd9075e2afddbba69a01f209412b5d8bbe38)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aliens-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
