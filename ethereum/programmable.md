---
token: Programmable
ticker: V4
network: ethereum
risk_score: 32
status: medium
date: 2026-08-03
---

# Programmable (V4) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 32/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/programmable-eth)

---

## Audit Summary

The UERC20 contract is an ERC-20 token designed for factory-based deployment. It leverages Solady's ERC20 implementation for efficiency and includes custom metadata functionality. The primary security concern identified is the critical dependency on `msg.sender` (expected to be a factory) for all initialization parameters, which could lead to a malformed token if deployed incorrectly or by a malicious entity. Additionally, the contract lacks internal validation for critical constructor parameters, relying solely on the factory. The contract is not upgradeable, which simplifies its security profile regarding upgrades.

> **Final Recommendation:** It is crucial to ensure that the factory contract responsible for deploying UERC20 tokens rigorously validates all parameters before token creation and strictly controls the deployment process. Consider adding defensive checks within the UERC20 constructor for critical parameters to enhance robustness. Thoroughly document the intended use of the `tokenURI()` function for this fungible token to prevent misunderstandings.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract demonstrates good architectural practices by inheriting from Solady's optimized ERC20 implementation and OpenZeppelin interfaces (7.1 Architecture, 7.2 Code Security). Core token… |
| **Governance / Economics** | 1/10 | High | The UERC20 contract is a basic ERC-20 token and does not implement any complex governance mechanisms or economic models (7.5 Governance, 7.4 Economic). Its functionality is limited to standard token… |
| **Upgrades** | 6/10 | Medium | The UERC20 contract is implemented as a standard, non-upgradeable contract (7.7 Upgrades). There are no proxy patterns (e.g., UUPS, Transparent) or other upgradeability mechanisms present. This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Critical Dependency on `msg.sender` for Initialization  *(Severity: High · Status: Unresolved)*

The `UERC20` constructor critically relies on `msg.sender` to be the `IUERC20Factory` and to correctly provide all initialization parameters via `getParameters()`. If the `UERC20` contract is deployed directly by an address other than the intended factory, or by a malicious contract mimicking the factory interface, the token could be initialized with arbitrary or incorrect properties (e.g., wrong name, symbol, decimals, or even minting to an unintended recipient). This design pattern places a high degree of trust in the caller during deployment (7.3 Access Control, 7.2 Code Security).

**Recommendation:** The factory contract should be designed to ensure that `UERC20` tokens are only deployed through its `createToken` function, potentially using `create2` with a salt derived from the parameters to prevent front-running and ensure deterministic addresses. The factory must perform comprehensive validation of all parameters before passing them to the token constructor. Consider adding a mechanism (e.g., an `onlyFactory` modifier if direct deployment is to be prevented, though this is complex for co…


### `L-01` — Lack of Internal Parameter Validation in Constructor  *(Severity: Low · Status: Unresolved)*

The `UERC20` constructor directly uses parameters obtained from `IUERC20Factory(msg.sender).getParameters()` without performing any internal validation. For instance, it does not check if `params.totalSupply` is greater than zero or if `params.recipient` is not the zero address before calling `_mint`. While the `ITokenFactory` interface defines errors for these conditions, relying solely on the factory's validation introduces a single point of failure. If a factory were to provide invalid parameters, the `_mint` call might revert, or the token could be created in an unusable state (7.2 Code Security).

**Recommendation:** Implement basic defensive validation checks within the `UERC20` constructor for critical parameters. For example, ensure `params.totalSupply > 0` and `params.recipient != address(0)` before proceeding with the `_mint` operation. This adds a layer of robustness, preventing the creation of malformed tokens even if the factory provides invalid inputs.


### `I-01` — `tokenURI()` Function for Fungible Token  *(Severity: Informational · Status: Unresolved)*

The `UERC20` contract implements a `tokenURI()` function, which is typically associated with ERC-721 (NFT) tokens to provide a URI pointing to off-chain metadata. While technically permissible, its inclusion in a fungible ERC-20 token is unusual and not part of the standard ERC-20 specification. This might lead to confusion or unexpected behavior for systems and wallets that primarily interact with ERC-20 tokens and do not anticipate this extension (7.1 Architecture).

**Recommendation:** Clearly document the purpose and intended use of the `tokenURI()` function for this fungible token. Ensure that any off-chain systems or front-ends interacting with this token are aware of this non-standard extension and how to interpret the returned metadata. If not strictly necessary, consider removing it to maintain strict ERC-20 compliance.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7987...24ee`](https://etherscan.io/address/0x7987f03462200b3d8a072e02c89a8a41dcb124ee) |
| **Network** | Ethereum |
| **Price** | $0.001535 |
| **24h Volume** | $515.4K |
| **Liquidity** | $138.3K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 6d |
| **Top-10 Holders** | 23.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 841 buys / 758 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xd9ca22573437a06a12d5c757b151aa1a76265c1dfdde4b76507233d7ad2b6df0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/programmable-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-03*
