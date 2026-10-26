---
token: Memento
ticker: DEXTF
network: base
risk_score: 53
status: medium
date: 2026-09-22
---

# Memento (DEXTF) — Smart Contract Security Analysis | Base

> **Risk Score: 53/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/memento-base)

---

## Audit Summary

The FactoryBurnMintERC20 contract implements a standard ERC20 token with additional burn and mint functionalities, managed by a role-based access control system. It incorporates OpenZeppelin's Ownable2Step for secure ownership management and includes a maximum supply limit. While the code demonstrates good practices like Solidity 0.8.x safety features and address validation, the highly centralized control over token supply and an inconsistency in initial supply validation present notable risks. The contract's integration with an external CCIP admin also introduces an external dependency that should be thoroughly understood.

> **Final Recommendation:** To enhance the security and decentralization of the FactoryBurnMintERC20 contract, consider implementing a multi-signature wallet for the owner address to manage critical functions like role assignments and the `s_ccipAdmin` setting. This would distribute control and reduce the risk associated with a single point of failure. Additionally, ensure that the `preMint` amount in the constructor is explicitly validated against the `maxSupply` to maintain tokenomics consistency from deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages well-audited OpenZeppelin libraries (v4.8.3) and Solidity 0.8.x, benefiting from built-in overflow/underflow checks (7.2 Code Security). The `validAddress` modifier prevents… |
| **Governance / Economics** | 4/10 | Medium | The contract's economic model is highly centralized, with the owner having complete control over granting and revoking minter/burner roles, directly impacting token supply (7.4 Economic). While a… |
| **Upgrades** | 3/10 | High | The FactoryBurnMintERC20 contract is not designed as an upgradeable proxy (7.7 Upgrades). This means its logic cannot be modified post-deployment, eliminating upgrade-specific risks but requiring… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 27.7% |
| **Top-3 Unlocked** | 68.5% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — `preMint` can Exceed `maxSupply` in Constructor  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `preMint` amount provided in the constructor is minted directly using `_mint(newOwner, preMint)` without checking against the `i_maxSupply` value. The `MaxSupplyExceeded` check is only applied to subsequent calls to the `mint` function. This allows the initial token supply to potentially exceed the declared `i_maxSupply` at deployment, leading to an inconsistent state where `totalSupply()` is greater than `maxSupply()` (7.2 Code Security, 7.4 Economic).

**Recommendation:** Add a check in the constructor to ensure that `preMint` does not exceed `maxSupply_` if `maxSupply_` is not zero. For example: ```solidity constructor(     // ... other params     uint256 maxSupply_,     uint256 preMint,     // ... other params ) ERC20(name, symbol) {     // ...     i_maxSupply = maxSupply_;     if (maxSupply_ != 0 && preMint > maxSupply_) {         revert MaxSupplyExceeded(preMint); // Or a custom error for constructor     }     if (preMint != 0) _mint(newOwner, preMint);…


### `M-02` — Centralized Control over Token Supply and Critical Roles  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `owner` address has complete control over granting and revoking `minter` and `burner` roles, as well as setting the `s_ccipAdmin` address. This centralization means a single compromised owner key or a malicious owner could manipulate the token supply (minting/burning) or redirect critical administrative functions through the `s_ccipAdmin` without any checks or balances. This introduces a significant single point of failure and trust assumption (7.3 Access Control, 7.4 Economic).

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the `owner` address to manage critical functions such as `grantMintRole`, `grantBurnRole`, `revokeMintRole`, `revokeBurnRole`, and `setCCIPAdmin`. This would require multiple approvals for sensitive operations, significantly reducing the risk of a single point of compromise or malicious action. Alternatively, explore a decentralized governance model if the project aims for greater decentralization.


### `L-01` — Unclear Role and Privileges of `s_ccipAdmin`  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract allows the `owner` to set an address for `s_ccipAdmin` via `setCCIPAdmin`. While this contract only provides a getter (`getCCIPAdmin`) and setter for this address, its actual privileges and interactions with other components of the Cross-Chain Interoperability Protocol (CCIP) are not defined within this codebase. This creates an implicit external dependency, and the security of the overall system relies on the proper management and behavior of the `s_ccipAdmin` in external contracts (7.6 External, 7.8 Operations).

**Recommendation:** Clearly document the intended role, responsibilities, and specific privileges of the `s_ccipAdmin` address within the broader CCIP ecosystem. Ensure that the entity controlling this address is highly secure and follows robust operational procedures. Consider adding comments in the code or external documentation to clarify its purpose.


### `I-01` — Redundant `decreaseApproval` and `increaseApproval` Aliases  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract includes `decreaseApproval` and `increaseApproval` functions that internally call `decreaseAllowance` and `increaseAllowance` respectively. While harmless, these aliases are not part of the standard ERC20 interface and might introduce slight confusion or redundancy without providing additional functionality (7.2 Code Security).

**Recommendation:** Consider removing these alias functions if they do not serve a specific purpose beyond simply calling the standard `decreaseAllowance` and `increaseAllowance`. If they are intended for backward compatibility or specific integration, document their purpose clearly.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb69b...fa89`](https://basescan.org/address/0xb69bbb15095c0949489fbb43951d2b750fa7fa89) |
| **Network** | Base |
| **Price** | $0.05966 |
| **24h Volume** | $88.9K |
| **Liquidity** | $190.4K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 48.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2152 buys / 1861 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xc3f617c8a3da6d286c8f97af946a8f293632c852)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/memento-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-22*
