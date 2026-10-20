---
token: PAAL AI
ticker: $PAAL
network: ethereum
risk_score: 7
status: low
date: 2026-09-23
---

# PAAL AI ($PAAL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/paal-ai-eth)

---

## Audit Summary

The PAALAI token contract implements a standard ERC-20 interface with a reflection/tax mechanism, including buy, sell, and transfer fees, and an automated swap-and-distribute feature. The contract exhibits a high degree of centralized control by the owner, who can manage critical parameters such as tax rates, swap settings, and tax wallet addresses. While mechanisms like `taxesAreLocked` can introduce immutability for certain parameters, the non-upgradeable nature of the contract means any discovered vulnerabilities or desired feature enhancements cannot be implemented without a full redeployment. The contract also relies on an external `Initializer` contract, introducing an additional trust dependency.

> **Final Recommendation:** To mitigate the risks associated with centralized control, consider implementing a multi-signature wallet for the `_owner` address to manage critical functions. Enhance transparency by emitting events for all significant state changes, such as modifications to tax rates, swap parameters, and tax wallet addresses. Thoroughly review and test all external contract interactions, especially with the `Initializer` contract, to ensure their security and intended behavior. Given the non-upgradeable nature, ensure comprehensive testing and formal verification are conducted before any future deployments.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract demonstrates a solid architectural foundation for an ERC-20 token with a reflection mechanism (7.1 Architecture). It incorporates common security patterns like the `inSwap` flag to… |
| **Governance / Economics** | 10/10 | Low | The contract exhibits a high degree of centralization, with the `onlyOwner` modifier controlling all critical parameters, including tax rates, swap thresholds, and tax wallet addresses (7.3 Access… |
| **Upgrades** | 10/10 | Low | The PAALAI contract is not designed to be upgradeable (7.7 Upgrades). This means that any discovered vulnerabilities, bugs, or desired feature enhancements cannot be patched or implemented without… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, UNCX |
| **Lock Expiry** | ✅ 2034 (verified ≥ 1 year) — UNCX V2 |

## Security Findings

_🟠 1 High · 🟡 3 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control and Single Point of Failure  *(Severity: High · Status: Unresolved)*

The `onlyOwner` modifier grants extensive control over critical contract parameters, including tax rates, swap thresholds, tax wallets, and the ability to enable/disable trading and contract swaps. This centralization presents a significant single point of failure. A compromise of the owner's private key could lead to malicious changes, such as setting exorbitant fees, redirecting tax funds, or disabling trading, severely impacting the protocol's integrity and user funds. (7.3 Access Control, 7.5 Governance)

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the `_owner` address to manage critical functions. This requires multiple trusted parties to approve transactions, significantly reducing the risk of a single point of compromise. Consider implementing time-locks for highly sensitive operations to allow users to react to pending changes.


### `M-01` — Unused `_isExcludedFromProtection` Mapping  *(Severity: Medium · Status: Unresolved)*

The `_isExcludedFromProtection` mapping is declared but not initialized or used anywhere in the provided contract code. This suggests either an incomplete feature implementation, a misunderstanding of intended functionality, or dead code. If it was intended for a specific protection mechanism (e.g., against bot attacks or certain transfer restrictions), its absence could lead to unexpected behavior or a lack of intended security. (7.2 Code Security)

**Recommendation:** Clarify the intended purpose of the `_isExcludedFromProtection` mapping. If it's an incomplete feature, either implement its functionality fully or remove the unused variable to improve code clarity and reduce potential confusion. If it's dead code, remove it.


### `M-02` — Potential for High Tax Rates and Economic Manipulation  *(Severity: Medium · Status: Unresolved)*

The contract allows the owner to set `buyFee`, `sellFee`, and `transferFee` up to `maxBuyTaxes`, `maxSellTaxes`, `maxTransferTaxes` (1000, meaning 10% when `masterTaxDivisor` is 10000). While the `taxesAreLocked` flag can prevent future changes, initially high or maliciously modified taxes could significantly impact token liquidity, trading volume, and user trust. The current default fees are 4% buy/sell, which is already substantial. (7.4 Economic, 7.3 Access Control)

**Recommendation:** Consider implementing a community-driven governance mechanism or a time-lock for changes to tax rates, even before `taxesAreLocked` is set. Clearly communicate the maximum potential tax rates to users. Ensure that the `taxesAreLocked` function is called promptly after launch to provide immutability and build user confidence.


### `M-03` — Dependency on External `Initializer` Contract  *(Severity: Medium · Status: Unresolved)*

The `PAALAI` contract relies on an external `Initializer` interface for critical functions like `setLaunch` and `setLpPair`. The security and trustworthiness of this external contract are paramount. If the `Initializer` contract is compromised, contains vulnerabilities, or behaves maliciously (e.g., setting a malicious LP pair or incorrect launch parameters), it could directly impact the `PAALAI` token's functionality, security, and economic stability. (7.6 External)

**Recommendation:** Conduct a thorough security audit of the `Initializer` contract. Ensure that the `Initializer` contract itself has robust access control, is immutable after its intended use, or is controlled by a highly secure multi-signature wallet. Clearly document the interaction model and trust assumptions regarding the `Initializer` contract.


### `L-01` — Lack of Event Emission for Critical State Changes  *(Severity: Low · Status: Unresolved)*

Several critical state changes, such as modifications to `_taxRates`, `_ratios`, `swapThreshold`, `swapAmount`, `piSwapPercent`, or `_taxWallets`, do not emit corresponding events. This makes it difficult for off-chain monitoring tools, block explorers, and users to track important configuration changes, reducing transparency and auditability of the contract's operational parameters. (7.2 Code Security, 7.8 Operations)

**Recommendation:** Emit events for all functions that modify critical state variables. This provides a transparent and auditable log of changes, enhancing user trust and enabling better monitoring by external services. For example, `event TaxRatesUpdated(uint16 buyFee, uint16 sellFee, uint16 transferFee);`.


### `L-02` — Hardcoded Tax Wallets in Constructor  *(Severity: Low · Status: Unresolved)*

The `_taxWallets` are hardcoded in the constructor. While the owner can change these addresses later via an `onlyOwner` function (assuming one exists, though not shown in the provided snippet), it's generally better practice to allow for more flexible initialization or to ensure these addresses are thoroughly vetted before deployment. If any of these addresses are incorrect or compromised at deployment, it could lead to misdirection of funds until the owner manually updates them. (7.2 Code Security, 7.8 Operations)

**Recommendation:** Ensure that all hardcoded addresses are meticulously verified before deployment. For future deployments, consider allowing the owner to set these addresses immediately after deployment through a dedicated initialization function, rather than hardcoding them, to provide more flexibility and reduce the risk of errors during deployment.


### `I-01` — Fixed-Point Arithmetic with `uint16` for Ratios/Fees  *(Severity: Informational · Status: Unresolved)*

The contract uses `uint16` for `_taxRates` and `_ratios` in conjunction with a `masterTaxDivisor` of `10000`. While this is functional and sufficient for the current fee structure (max 10%), `uint16` has a maximum value of 65535. This design choice limits the maximum possible fee/ratio to 6.5535% (65535 / 10000). This is a design constraint that might limit future flexibility if significantly higher precision or larger fee values were ever considered, though it is unlikely for typical tokenomics. (7.2 Code Security)

**Recommendation:** This is a design choice and not a vulnerability. Document this limitation clearly within the project's specifications. If there's a future need for higher precision or larger fee values, consider using `uint256` for these variables, although it would slightly increase gas costs for storage and operations.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x14fe...0e16`](https://etherscan.io/address/0x14fee680690900ba0cccfc76ad70fd1b95d10e16) |
| **Network** | Ethereum |
| **Price** | $0.008273 |
| **24h Volume** | $87.4K |
| **Liquidity** | $1.12M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 36.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 163 buys / 118 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x2a6c340bcbb0a79d3deecd3bc5cbc2605ea9259f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/paal-ai-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-23*
