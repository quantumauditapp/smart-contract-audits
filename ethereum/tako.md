---
token: Tako
ticker: TAKO
network: ethereum
risk_score: 0
status: low
date: 2026-09-12
---

# Tako (TAKO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tako-eth)

---

## Audit Summary

The TAKO contract is an ERC-20 token with custom tax mechanisms, anti-bot features, and automated liquidity management. A critical issue identified is that the provided source code is incomplete, specifically the `_transfer` function is truncated, and the `swapTokensForEth` and `sendETHToFee` functions are missing. This prevents a comprehensive security assessment of core functionalities, particularly tax distribution and liquidity operations. Additionally, the contract exhibits high centralization of control by the owner over critical parameters.

> **Final Recommendation:** A complete and verifiable source code must be provided to conduct a thorough security audit. Without the full implementation of core functions like `_transfer`, `swapTokensForEth`, and `sendETHToFee`, the contract's security posture cannot be accurately assessed, and it should be considered high-risk. Address the high centralization of control by considering multi-signature wallets or time-locks for critical administrative functions. Implement comprehensive event emissions for all parameter changes to enhance transparency and off-chain monitoring.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1) includes standard ERC-20 functionality with custom tax and anti-bot logic. Code security (7.2) is severely impacted by the incomplete source code, making it… |
| **Governance / Economics** | 9/10 | Low | The contract's economic model (7.4) relies heavily on dynamic tax rates and automated liquidity provisions, which are highly configurable by the owner. Governance (7.5) is centralized, with the owner… |
| **Upgrades** | 10/10 | Low | The contract is not designed with an upgradeable proxy pattern (7.7), meaning its logic cannot be changed after deployment. This eliminates upgrade-related risks such as proxy misconfigurations or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 4 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Owner's Ability to Manipulate Dynamic Tax and Swap Thresholds  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract features dynamic tax rates (`_initialBuyTax`, `_finalBuyTax`, `_reduceBuyTaxAt`, `_initialSellTax`, `_finalSellTax`, `_reduceSellTaxAt`) and a `_preventSwapBefore` threshold, all configurable by the owner. While providing flexibility, the owner's ability to change these parameters at any time without a time-lock or community vote can lead to unpredictable trading conditions, sudden changes in tokenomics, or even manipulation of the automated swap mechanism, potentially impacting user trust and token value.

**Recommendation:** Implement time-locks for changes to critical economic parameters to provide transparency and allow users to react to upcoming changes. Consider a more decentralized governance model for such sensitive parameters if the project aims for long-term community trust. Clearly document the intended values and adjustment policies for these parameters.


### `M-02` — Incomplete Contract Code Provided  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided Solidity source code is incomplete. Specifically, the `_transfer` function is truncated at `_balances[address(this)]=_bala...`, and the `swapTokensForEth` and `sendETHToFee` functions, which are called within the `_transfer` function's automated swap logic, are entirely missing. This prevents a full and accurate security assessment of the contract's core token transfer, tax distribution, and liquidity management mechanisms.

**Recommendation:** Provide the complete and verified source code for all contract functions, including the full `_transfer` implementation and the definitions of `swapTokensForEth` and `sendETHToFee`. A full audit cannot be completed without this information.


### `M-03` — High Centralization of Control by Owner  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `Ownable` contract grants the deployer (owner) extensive control over critical contract parameters and functionalities. The owner can modify tax rates (`setInitialBuyTax`, `setFinalBuyTax`, `setTransferTax`), transaction limits (`setMaxTxAmount`, `setMaxWalletSize`), trading status (`openTrading`, `setSwapEnabled`), bot lists (`setBots`, `delBots`), and even the Uniswap router address (`updateUniswapV2Router`). This high degree of centralization creates a single point of failure and a significant trust dependency on the owner, who could maliciously or inadvertently alter the contract's behavior.

**Recommendation:** Consider implementing a multi-signature wallet for critical administrative functions or introducing time-locks for sensitive parameter changes. This would add a layer of security and decentralization, reducing the risk associated with a single point of control. Clearly document the owner's capabilities and the intended use of these powerful functions.


### `M-04` — Potential for Denial of Service in Sell Limiting Mechanism  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_transfer` function includes a mechanism (`sellCount` and `lastSellBlock`) that limits the number of sells to 3 per block (`require(sellCount < 3, "Only 3 sells per block!");`). While intended to prevent bot spam or manipulation, this hardcoded limit can lead to legitimate users being unable to sell their tokens if the block's sell quota is reached by other transactions. This effectively creates a temporary denial of service for subsequent sellers within the same block.

**Recommendation:** Re-evaluate the necessity and implementation of the sell limiting mechanism. If such a limit is critical, consider alternative approaches that are less prone to causing denial of service for legitimate users, such as dynamic limits based on volume or time-based cooldowns per address, rather than per block. If kept, clearly communicate this limitation to users.


### `L-01` — Redundant SafeMath Library Usage  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract utilizes the `SafeMath` library for arithmetic operations. However, the contract is compiled with Solidity version 0.8.23, which includes native overflow and underflow checks by default. This makes the explicit use of `SafeMath` redundant, as the compiler would already revert on such conditions. While not a vulnerability, it adds unnecessary code and slightly increases gas costs due to extra checks.

**Recommendation:** Remove the `SafeMath` library and its `using SafeMath for uint256;` directive. Rely on Solidity's native overflow/underflow protection for `uint256` operations. This will simplify the code and potentially reduce gas consumption slightly.


### `I-01` — Lack of Event Emission for Critical Parameter Changes  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). Several owner-controlled functions that modify critical contract parameters (e.g., `setTaxWallet`, `setInitialBuyTax`, `setInitialSellTax`, `setMaxTxAmount`, `setMaxWalletSize`, `setTaxSwapThreshold`, `setPreventSwapBefore`, `setBots`, `delBots`, `openTrading`, `setSwapEnabled`, `updateUniswapV2Router`) do not emit corresponding events. Without events, it is difficult for off-chain applications, block explorers, or users to monitor and track changes to the contract's configuration and behavior.

**Recommendation:** Emit specific events whenever a critical contract parameter is changed by the owner. These events should include the old value, the new value, and the address of the caller. This enhances transparency and allows for better off-chain monitoring and auditing of administrative actions.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0ee3...af0a`](https://etherscan.io/address/0x0ee375090f423934ebfbb241a3eb2ee4e01eaf0a) |
| **Network** | Ethereum |
| **Price** | $0.00000055 |
| **24h Volume** | $49.0K |
| **Liquidity** | $50.2K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 61.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 283 buys / 90 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x0cff36ee76f2ea83064863b2ef19fe84d6f46417)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tako-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
