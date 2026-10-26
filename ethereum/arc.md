---
token: ARC
ticker: ARC
network: ethereum
risk_score: 56
status: medium
date: 2026-09-17
---

# ARC (ARC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/arc-eth)

---

## Audit Summary

The ARCEnhanced contract implements an upgradeable ERC20 token with standard OpenZeppelin extensions, including burnable, pausable, permit, and voting functionalities. A key feature is the integration of an external `ITaxModule` contract, which can apply taxes on token transfers. While the contract utilizes well-audited OpenZeppelin libraries and a standard UUPS upgrade pattern, the critical dependency on the external `ITaxModule` introduces significant economic and operational risks due to its ability to manipulate transfer amounts and potentially block transactions. Centralized control by the owner over the `taxModule` further amplifies these risks.

> **Final Recommendation:** It is strongly recommended to conduct a comprehensive audit of the `ITaxModule` contract to fully understand its security posture, economic implications, and access control mechanisms, as it is a critical dependency for the ARCEnhanced token. For enhanced security and decentralization, consider implementing a multi-signature wallet for the contract's ownership and for managing the `taxModule` address. Additionally, introduce a timelock for changes to the `taxModule` to provide users with a window to react to significant operational changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages battle-tested OpenZeppelin libraries for ERC20, upgradeability (UUPS), and access control (Ownable), contributing to a solid technical foundation (7.1 Architecture, 7.2 Code… |
| **Governance / Economics** | 2/10 | High | The contract employs an `Ownable` access control pattern, granting the owner significant power over critical functions such as pausing/unpausing transfers and managing the `taxModule` (7.3 Access… |
| **Upgrades** | 3/10 | High | The contract correctly implements the UUPS upgradeability pattern using OpenZeppelin's `UUPSUpgradeable` module (7.7 Upgrades). The `_authorizeUpgrade` function is appropriately restricted to the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control over Tax Module  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `owner` has sole authority to set and remove the `taxModule` via `setTaxModule` and `removeTaxModule` functions. This centralization allows a single entity to introduce or remove a contract that can arbitrarily tax or block all token transfers, posing a significant economic and operational risk to token holders. A compromised owner key could lead to severe consequences (7.3 Access Control, 7.5 Governance, 7.8 Operations).

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the contract's ownership. Additionally, consider introducing a timelock mechanism for `setTaxModule` and `removeTaxModule` functions to provide a delay before changes take effect, allowing the community to react to potentially malicious or erroneous updates.


### `M-02` — Critical Dependency on External Tax Module  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ARCEnhanced` token's core transfer logic in the `_update` function is critically dependent on the external `ITaxModule` contract. The `processTransfer` function of `ITaxModule` dictates the `netAmount` of tokens transferred and the `taxCollector` address. A malicious or compromised `ITaxModule` could manipulate transfer amounts (e.g., return `0` for `netAmount` to effectively burn tokens, or return an incorrect `netAmount`), block transfers by reverting, or redirect funds to an unauthorized `taxCollector`, severely impacting the token's functionality and economic stability (7.6 External, 7.4 Economic).

**Recommendation:** Implement robust validation and safeguards for the `taxModule` address, such as a timelock for `setTaxModule` changes. Crucially, a thorough security audit of the `ITaxModule` implementation is paramount to ensure its integrity and prevent potential exploits. Consider implementing circuit breakers or emergency mechanisms within `ARCEnhanced` to disable the tax system if the `ITaxModule` misbehaves.


### `L-01` — Lack of Robust Input Validation for `setTaxModule`  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `setTaxModule` function only checks that the `_taxModule` address is not `address(0)`. There is no further validation to ensure that the provided address actually implements the `ITaxModule` interface correctly or behaves as expected. Setting an arbitrary contract address that does not conform to the interface or contains malicious logic could lead to unexpected reverts in `_update` or incorrect tax calculations, effectively disrupting token transfers (7.2 Code Security).

**Recommendation:** Enhance the `setTaxModule` function with more robust validation. This could include checking for specific function selectors (e.g., `ITaxModule(newModule).processTransfer.selector`) or using `try-catch` blocks during a test call to ensure the new module responds as expected before setting it. Alternatively, ensure that any `ITaxModule` implementation is thoroughly audited and whitelisted.


### `I-01` — Unspecified `ITaxModule` Access Control and Governance  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ITaxModule` interface includes critical functions such as `setTaxRates`, `setTaxCollector`, `setTaxEnabled`, `setTaxExemption`, and `emergencyDisableTax`. The access control and governance mechanisms for these functions within the `ITaxModule` contract itself are not specified in the provided `ARCEnhanced` code. This creates an implicit dependency on the `ITaxModule`'s internal security and governance, which is outside the scope of this audit (7.5 Governance, 7.6 External).

**Recommendation:** Ensure the `ITaxModule` contract has robust and transparent access control mechanisms, ideally a multi-signature wallet or a well-defined governance process, to manage its critical parameters. The ownership and control of the `ITaxModule` should be clearly documented and understood by all stakeholders.


### `I-02` — Hardcoded Token Name and Symbol  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The token name 'ARC' and symbol 'ARC' are hardcoded within the `initialize` function using `__ERC20_init("ARC", "ARC")` and `__ERC20Permit_init("ARC")`. While this is a common practice for ERC20 tokens, it means these values cannot be changed without performing a contract upgrade (7.1 Architecture).

**Recommendation:** This is a design choice and not a vulnerability. If flexibility to change the token name or symbol post-deployment is ever desired, these values would need to be stored in state variables and managed by an owner-controlled function, which would require an upgrade to the current implementation.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x672f...f499`](https://etherscan.io/address/0x672fdba7055bddfa8fd6bd45b1455ce5eb97f499) |
| **Network** | Ethereum |
| **Price** | $0.00215 |
| **24h Volume** | $199.9K |
| **Liquidity** | $122.6K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 58.9% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 506 buys / 289 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xfa39ea4ad8893ce6e8b119ba4b7532a70d137c4a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/arc-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-17*
