---
token: HarryPotterObamaSonic10Inu
ticker: BITCOIN
network: ethereum
risk_score: 69
status: high
date: 2026-07-29
---

# HarryPotterObamaSonic10Inu (BITCOIN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 69/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/harrypotterobamasonic10inu-eth)

---

## Audit Summary

The HarryPotterObamaSonic10Inu (BITCOIN) token contract exhibits severe centralization risks and potential for malicious actions by the owner. While standard ERC-20 functionality is present, the extensive administrative control over taxes, trading, and user blacklisting poses critical security and economic threats to token holders. The contract is not upgradeable, making these risks permanent.

> **Final Recommendation:** Given the critical centralization risks, it is strongly recommended that the project team consider a complete redesign of the token contract to decentralize control over critical parameters. Implement multi-signature wallets for sensitive administrative functions, or better yet, remove the ability to unilaterally modify taxes, transaction limits, and user blacklists. If such extensive control is deemed necessary, transparent communication and robust governance mechanisms should be established to ensure community oversight and prevent malicious actions. Users should be made fully aware of the inherent risks associated with such a highly centralized token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 2/10 | High | The contract implements a standard ERC-20 token with additional features like transaction taxes, anti-whale limits, and anti-bot mechanisms (7.2 Code Security). It utilizes SafeMath for arithmetic… |
| **Governance / Economics** | 5/10 | Medium | The contract's economic model is highly centralized and vulnerable to owner manipulation (7.4 Economic). The owner has absolute control over critical parameters, including the ability to set buy and… |
| **Upgrades** | 6/10 | Medium | The contract is not designed with an upgrade mechanism (7.7 Upgrades). This means that once deployed, its logic cannot be altered. While this eliminates upgrade-related risks, it also means that any… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — TeamFinance |
| **Top-1 Unlocked Holder** | 0.0% |

## Security Findings

_🔴 3 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Owner Can Set Taxes to 100% (Rug Pull Vector)  *(Severity: Critical · Status: Unresolved)*

The `setTaxes` function allows the contract owner to set `_initialBuyTax`, `_initialSellTax`, `_finalBuyTax`, and `_finalSellTax` to arbitrary values. This includes the ability to set taxes to 100%, which would effectively prevent users from selling their tokens (100% sell tax) or buying new tokens (100% buy tax). This constitutes a direct rug pull vector, allowing the owner to drain liquidity or freeze user funds.

**Recommendation:** Remove or significantly restrict the owner's ability to modify tax percentages. If taxes are a core part of the tokenomics, they should be immutable or subject to a decentralized governance mechanism with a timelock. If mutable, implement strict upper bounds (e.g., max 25%) to prevent malicious exploitation.


### `C-02` — Owner Can Blacklist/Whitelist Any Address  *(Severity: Critical · Status: Unresolved)*

The `setBots` function allows the contract owner to add or remove any address from the `bots` mapping. Addresses marked as 'bots' are prevented from transferring tokens in the `_transfer` function. This grants the owner the power to arbitrarily blacklist any user, effectively freezing their tokens and preventing them from participating in trading. This is a severe centralization and censorship risk.

**Recommendation:** Remove the `setBots` function entirely. Decentralized tokens should not have the ability to arbitrarily freeze user funds or prevent transfers. If anti-bot measures are desired, they should be implemented in a non-custodial and transparent manner, ideally without direct owner intervention on individual addresses.


### `C-03` — Owner Can Manipulate Trading and Liquidity  *(Severity: Critical · Status: Unresolved)*

The `openTrading` function, callable only by the owner, initializes the Uniswap router and pair, and enables trading. This gives the owner complete control over when trading starts. Furthermore, the owner can update `_maxTxAmount`, `_maxWalletSize`, `_taxSwapThreshold`, and `_maxTaxSwap` at any time. This allows the owner to manipulate market conditions, prevent large transactions, or even halt trading by setting prohibitive limits, leading to potential market manipulation and denial of service for users.

**Recommendation:** Decentralize or remove the `openTrading` function. Once trading is enabled, critical parameters like transaction limits and swap thresholds should be immutable or controlled by a decentralized governance mechanism with a timelock. If mutable, implement reasonable bounds and timelocks for changes.


### `H-01` — Centralized Control Over Fee Exclusions  *(Severity: High · Status: Unresolved)*

The `excludeFromFee` function allows the owner to exempt any address from paying transaction fees. While the owner, contract, and tax wallet are initially excluded, the ability to add arbitrary addresses to this exclusion list introduces a significant centralization risk. The owner could exclude favored addresses or even themselves from all taxes, creating an unfair advantage or enabling further manipulation.

**Recommendation:** Limit fee exclusion to essential protocol addresses (e.g., the contract itself, the liquidity pair). If other exclusions are necessary, they should be immutable or subject to a transparent, decentralized governance process.


### `H-02` — Transfer Delay Can Be Arbitrarily Enabled/Disabled  *(Severity: High · Status: Unresolved)*

The `setTransferDelayEnabled` function allows the owner to enable or disable the `transferDelayEnabled` mechanism at will. This mechanism, when active, prevents holders from transferring tokens within a certain timeframe after their last transfer. While intended as an anti-dump measure, the owner's unilateral control over its activation/deactivation can be used to selectively hinder trading for certain periods, potentially impacting market stability or user liquidity without warning.

**Recommendation:** If a transfer delay is a core feature, its activation and deactivation should be immutable or controlled by a decentralized governance mechanism with a timelock. Arbitrary owner control over such a significant trading restriction is a high risk.


### `M-01` — Potential for Stuck ETH in `swapAndLiquify`  *(Severity: Medium · Status: Unresolved)*

In the `swapAndLiquify` function, after `swapTokensForEth` is called, the contract attempts to add liquidity and then transfer the remaining ETH to `_taxWallet`. If the `addLiquidity` call fails (e.g., due to slippage, insufficient ETH, or external router issues), the remaining ETH might not be fully utilized for liquidity. While `_taxWallet.transfer` attempts to send the remaining balance, if `_taxWallet` is a contract that rejects ETH, or if there's an unexpected revert, some ETH could become stuck in the contract, requiring manual `rescueETH` by the owner.

**Recommendation:** Implement more robust error handling or fallback mechanisms within `swapAndLiquify`. Consider adding checks for successful liquidity addition and potentially a retry mechanism or a more explicit way to handle leftover ETH if `addLiquidity` fails. Ensure `_taxWallet` is capable of receiving ETH or add a fallback for rejected transfers.


### `L-01` — Missing SPDX License Identifier  *(Severity: Low · Status: Unresolved)*

The contract uses `// SPDX-License-Identifier: NONE`. While technically valid, it's generally recommended to use a standard SPDX license identifier (e.g., MIT, GPL-3.0) to clarify the licensing terms of the code. Using 'NONE' can lead to ambiguity regarding intellectual property rights and usage permissions.

**Recommendation:** Replace `// SPDX-License-Identifier: NONE` with a standard and appropriate SPDX license identifier, such as `// SPDX-License-Identifier: MIT`.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x72e4...eea9`](https://etherscan.io/address/0x72e4f9f808c49a2a61de9c5896298920dc4eeea9) |
| **Network** | Ethereum |
| **Price** | $0.009394 |
| **24h Volume** | $295.1K |
| **Liquidity** | $708.4K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 3y |
| **Top-10 Holders** | 30.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 509 buys / 485 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x25392d7129040710f152174af5019004a6f9b18d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/harrypotterobamasonic10inu-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-29*
