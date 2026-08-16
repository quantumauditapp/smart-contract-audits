---
token: Banana
ticker: BANANA
network: ethereum
risk_score: 100
status: critical
date: 2026-08-16
---

# Banana (BANANA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/banana-eth)

---

## Audit Summary

The Banana token contract implements an ERC-20 standard with significant deflationary and anti-whale mechanics, including transaction fees, max transaction limits, and automated liquidity provision. The audit identified critical centralization risks due to extensive owner privileges, an expired liquidity pool lock, and a lack of slippage protection in automated swaps. High transaction fees and the owner's ability to change the Uniswap pair also pose substantial economic and security risks. While basic reentrancy protection is present, the overall design grants the owner excessive control, making the protocol highly susceptible to malicious actions or economic instability.

> **Final Recommendation:** Address the critical centralization risks by implementing a robust, decentralized governance mechanism or by renouncing ownership after setting immutable, safe parameters. Immediately re-lock the liquidity pool for a substantial period to protect investors from a rug pull. Implement proper slippage protection (`amountOutMin` > 0) in all automated swap functions to prevent value loss from sandwich attacks and high slippage. Re-evaluate the economic model, specifically the extremely high transaction fees, to ensure sustainability and attract legitimate users.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 2/10 | High | The contract utilizes Solidity 0.8.21, benefiting from built-in overflow/underflow protection. It includes a `swapping` flag to prevent reentrancy during automated liquidity operations, addressing a… |
| **Governance / Economics** | 1/10 | High | The economic model is highly centralized, with the owner possessing extensive control over critical parameters such as transaction fees, max transaction amounts, and wallet limits (7.3 Access… |
| **Upgrades** | 4/10 | Medium | The contract is not designed as an upgradeable proxy (7.7 Upgrades). Therefore, there are no upgrade-specific risks or considerations. Any changes to the contract logic would require a new deployment… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, UNCX |
| **Lock Expiry** | Expired 335d ago |

## Security Findings

_🔴 3 Critical · 🟠 2 High · 🟡 2 Medium · ⚪ 1 Informational_

### `C-01` — Expired Liquidity Pool Lock Poses Rug Pull Risk  *(Severity: Critical · Status: Unresolved)*

The provided prefill data indicates that the liquidity pool (LP) lock for the Uniswap V2 pair has expired. This means that the initial liquidity provider, likely the contract owner or an associated address, can withdraw all liquidity from the pool at any time. Such an action would lead to a complete collapse of the token's price, resulting in a total loss for token holders.

**Recommendation:** Immediately re-lock the liquidity for a significant duration (e.g., 1-5 years) using a reputable locker service. Provide verifiable proof of the new lock to the community to restore trust and mitigate the rug pull risk.


### `C-02` — Lack of Slippage Protection in Automated Swaps  *(Severity: Critical · Status: Unresolved)*

The `swapAndLiquify` function calls `uniswapV2Router.swapExactTokensForETHSupportingFeeOnTransferTokens` with `amountOutMin` set to `0`. This lack of slippage protection means that the contract is vulnerable to sandwich attacks and high price impact during automated token swaps. Malicious actors can front-run and back-run these transactions, extracting value and causing the contract to receive significantly less ETH than expected for the swapped tokens, ultimately harming the protocol's liquidity and value.

**Recommendation:** Implement a reasonable `amountOutMin` value in the `swapExactTokensForETHSupportingFeeOnTransferTokens` call within `swapAndLiquify`. This value should be calculated based on the expected ETH output and a tolerable slippage percentage, protecting the contract from excessive losses due to market manipulation.


### `C-03` — Excessive Owner Privileges and Centralization Risk  *(Severity: Critical · Status: Unresolved)*

The `owner()` address has extensive control over critical contract parameters, including the ability to set `buyTotalFees`, `sellTotalFees`, `revFee`, `treasuryFee`, `teamFee`, `maxTransactionAmount`, `maxWallet`, `swapTokensAtAmount`, `limitsInEffect`, `launched`, and to add/remove addresses from fee and transaction limit exclusions. The owner can also update the `uniswapV2Pair` to an arbitrary address. This high degree of centralization presents a significant risk of malicious actions, such as draining funds, manipulating tokenomics, or disabling trading, leading to a potential rug pull or severe economic instability.

**Recommendation:** Consider implementing a decentralized governance mechanism (e.g., a multi-signature wallet or a DAO) for critical parameter changes. If decentralization is not feasible, clearly document the owner's responsibilities and consider time-locks or multi-party approvals for highly sensitive functions to reduce single-point-of-failure risks. Renouncing ownership without a robust governance system is not recommended given the current level of control.


### `H-01` — High Transaction Fees Detrimental to Adoption  *(Severity: High · Status: Unresolved)*

The contract implements extremely high transaction fees, with `buyTotalFees` and `sellTotalFees` both set to 40%. Such high fees are economically unsustainable for a cryptocurrency token and will severely deter legitimate trading activity. This can lead to low liquidity, reduced adoption, and a perception of the token as a speculative asset rather than a viable medium of exchange, ultimately harming its long-term value and stability.

**Recommendation:** Significantly reduce transaction fees to a more reasonable and competitive level (e.g., 1-10%). High fees often discourage trading and can lead to a 'dead' chart. A sustainable fee structure is crucial for fostering a healthy trading environment and encouraging adoption.


### `H-02` — Owner Can Change Uniswap Pair to Arbitrary Address  *(Severity: High · Status: Unresolved)*

The `updateUniswapV2Pair` function allows the owner to set the `uniswapV2Pair` address to any arbitrary address. A malicious owner could point this to a controlled contract or a non-existent address, effectively disrupting the automated liquidity provision mechanism, preventing swaps, or even draining funds if the new address is a malicious contract designed to exploit interactions.

**Recommendation:** Restrict the `updateUniswapV2Pair` function to only allow setting a new pair if it has been properly created and verified, or remove the ability to change the pair after initial deployment if the intention is for it to be immutable. If the functionality is necessary, consider adding a time-lock or multi-signature approval for such a critical change.


### `M-01` — Hardcoded External Contract Addresses  *(Severity: Medium · Status: Unresolved)*

The contract hardcodes the addresses for `IUniswapV2Router02` (0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D) and `WETH` (0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2). While these are standard addresses on Ethereum mainnet, hardcoding them makes the contract less flexible. In the event of a router upgrade, a WETH contract change, or deployment to a different network with different addresses, the contract would need to be redeployed, which is not possible for a non-upgradeable contract.

**Recommendation:** For future contracts, consider making such critical external addresses configurable by the owner (with appropriate access controls and safeguards) or through a governance mechanism. For this deployed contract, this is a limitation that cannot be changed without redeployment.


### `M-02` — `renounceOwnership` Without Replacement Mechanism  *(Severity: Medium · Status: Unresolved)*

The `Ownable` contract includes a `renounceOwnership` function, which, if called, sets the contract owner to `address(0)`. Given the extensive owner privileges in the `Banana` contract (e.g., setting fees, limits, managing exclusions, updating the Uniswap pair), renouncing ownership without a robust, decentralized governance mechanism in place would render the contract unmanageable. This could prevent necessary parameter adjustments, bug fixes, or responses to unforeseen circumstances.

**Recommendation:** If the intention is to decentralize control, ensure a fully functional and tested governance system (e.g., a DAO or a multi-signature wallet) is in place and capable of managing all critical parameters before `renounceOwnership` is ever considered. Otherwise, the owner should retain control to manage the contract's parameters responsibly.


### `I-01` — Unnecessary `pragma experimental ABIEncoderV2;`  *(Severity: Informational · Status: Unresolved)*

The `pragma experimental ABIEncoderV2;` directive is included in the contract. `ABIEncoderV2` is no longer experimental since Solidity version 0.8.0. While its presence is harmless, it is no longer necessary for Solidity 0.8.21 and can be removed for cleaner code.

**Recommendation:** Remove the `pragma experimental ABIEncoderV2;` directive.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x38e6...30b4`](https://etherscan.io/address/0x38e68a37e401f7271568cecaac63c6b1e19130b4) |
| **Network** | Ethereum |
| **Price** | $3.8700 |
| **24h Volume** | $488.6K |
| **Liquidity** | $2.69M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 2y |
| **Top-10 Holders** | 74.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 250 buys / 249 sells |

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

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x43de4318b6eb91a7cf37975dbb574396a7b5b5c6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/banana-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-16*
