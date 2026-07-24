---
token: BankrCoin
ticker: BNKR
network: base
risk_score: 19
status: low
date: 2026-06-10
---

# BankrCoin (BNKR) — Smart Contract Security Analysis | Base

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bankrcoin-base)

---

## Audit Summary

The Clanker protocol consists of a factory contract (`Clanker`) for deploying new ERC20 `Token` contracts, creating Uniswap V3 liquidity pools, and locking LP tokens. The audit identified a High-severity centralization risk due to the `onlyOwner` restriction on token deployment, a Medium-severity technical design flaw related to an arbitrary `weth` address requirement, and several Low-severity issues concerning parameter immutability and external call handling. The contract leverages established libraries like OpenZeppelin and Uniswap V3, contributing to its foundational security. Recommendations focus on decentralizing control, improving parameter flexibility, and enhancing robustness.

> **Final Recommendation:** To enhance the security and decentralization of the Clanker protocol, it is strongly recommended to address the identified centralization risks. Consider implementing a more decentralized token deployment mechanism, such as a permissionless factory or a multi-signature governance system for critical operations. Review and introduce flexibility for key economic parameters like `defaultLockingPeriod` and fee rates, allowing them to be adjusted through a secure, controlled process. Additionally, evaluate the necessity and implications of the `address(token) < weth` requirement, as it introduces unnecessary complexity and potential friction for users.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The technical architecture (7.1) utilizes a factory pattern with `create2` for predictable token addresses and integrates with Uniswap V3 for liquidity. Code security (7.2) benefits from Solidity… |
| **Governance / Economics** | 6/10 | Medium | Access control (7.3) is heavily centralized, with the `deployToken` function restricted to `onlyOwner` (H-01), giving the contract owner sole control over new token creation and liquidity… |
| **Upgrades** | 9/10 | Low | The `Clanker` contract is not designed as an upgradeable proxy, meaning its logic is immutable once deployed. The `Token` contracts are deployed via `create2` and are also immutable. Therefore, there… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.1% |
| **Top-3 Unlocked** | ⚠️ 99.4% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 3 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control over Token Deployment  *(Severity: High · Status: Unresolved)*

The `deployToken` function, which is responsible for creating new `Token` contracts, establishing Uniswap V3 liquidity pools, and locking LP tokens, is restricted to `onlyOwner`. This means that only the contract owner can initiate the creation of new tokens and their associated liquidity. This centralization introduces a single point of failure, limits the protocol's decentralization, and could lead to censorship or bottlenecks in token creation.

**Recommendation:** Consider decentralizing the token deployment process. Options include: 1) Removing the `onlyOwner` modifier to allow anyone to deploy tokens (if appropriate for the protocol's design). 2) Implementing a multi-signature wallet or a decentralized autonomous organization (DAO) for approving token deployments. 3) Introducing a whitelisting mechanism for trusted deployers, managed by a multi-sig or DAO.


### `M-01` — Arbitrary `weth` Address Requirement for Token Deployment  *(Severity: Medium · Status: Unresolved)*

The `deployToken` function includes a `require(address(token) < weth, "Invalid salt");` condition. This forces the deployed token's address (determined by `create2` with a user-provided `_salt`) to be numerically less than the `weth` address. This arbitrary requirement can significantly increase the computational burden and gas costs for users attempting to find a valid `_salt` that satisfies this condition. In some scenarios, it might even make it practically impossible to deploy a token if `weth` has a very low address, hindering legitimate token creation.

**Recommendation:** Re-evaluate the necessity of the `address(token) < weth` requirement. If it serves no critical security or functional purpose, it should be removed to improve usability and reduce deployment costs. If there is a specific architectural reason, consider alternative, less restrictive methods to achieve the desired consistency, or provide tools to assist users in generating valid salts efficiently.


### `L-01` — Immutability of Key Economic Parameters  *(Severity: Low · Status: Unresolved)*

The `defaultLockingPeriod` and `lpFeesCut` variables are set during the constructor and are not provided with setter functions. This makes them immutable after deployment. While immutability can offer predictability, the lack of flexibility might become an issue if market conditions, regulatory requirements, or protocol strategies necessitate adjustments to these parameters in the future. This could lead to the protocol becoming rigid or requiring a full redeployment to adapt.

**Recommendation:** Consider adding owner-controlled setter functions for `defaultLockingPeriod` and `lpFeesCut`. These setters should include appropriate access control (e.g., `onlyOwner`) and potentially a timelock or a multi-signature approval mechanism for sensitive changes to ensure security and provide a grace period for users to react.


### `L-02` — Immutability of `taxCollector` and `bundleFeeSwitch`  *(Severity: Low · Status: Unresolved)*

The `taxCollector` address is set in the constructor and is immutable. If this address is initially set incorrectly (e.g., to a non-existent address, a contract that cannot receive ETH, or a malicious address), the fee collection mechanism (`bundleFeeSwitch`) could be permanently broken or funds could be misdirected. Similarly, the `bundleFeeSwitch` itself is a public variable without a setter, making its state (whether fees are collected or not) immutable after deployment. This lack of configurability for a critical economic parameter limits the protocol's adaptability.

**Recommendation:** Implement owner-controlled setter functions for both `taxCollector` and `bundleFeeSwitch`. For `taxCollector`, ensure the setter includes input validation (e.g., `require(newTaxCollector != address(0))`). For both, consider adding a timelock or multi-signature approval for changes to enhance security and provide transparency.


### `L-03` — Unchecked Return Values of External Calls  *(Severity: Low · Status: Unresolved)*

While the `call` to `taxCollector` explicitly checks its success, some other external calls to Uniswap V3 components (e.g., `uniswapV3Factory.createPool`, `positionManager.mint`, `liquidityLocker.deploy`, `ILocker(lockerAddress).initializer`) and `ISwapRouter.exactInputSingle` do not explicitly check their return values. Although these are typically interface calls that revert on failure, explicit checks or `try/catch` blocks can provide additional robustness and clearer error handling, especially for calls to external, potentially less trusted, contracts.

**Recommendation:** For critical external calls, consider adding explicit checks for return values or wrapping them in `try/catch` blocks to handle potential failures gracefully. This can improve the contract's resilience against unexpected behavior from external dependencies.


### `I-01` — `deprecated` Flag Lifecycle Management  *(Severity: Informational · Status: Unresolved)*

The `deprecated` flag, controllable by the owner, prevents new token deployments when set to `true`. However, there is no mechanism to un-deprecate the contract. While this might be an intentional design choice for a final shutdown, it means that once deprecated, the factory cannot resume its primary function without a new deployment. The contract also does not specify how existing tokens or liquidity pools are affected or managed after deprecation.

**Recommendation:** Clarify the intended lifecycle of the `deprecated` flag. If temporary deprecation is desired, implement a function to revert the flag. If permanent, ensure documentation clearly states this. Additionally, consider adding logic or documentation regarding the implications of deprecation on existing deployed tokens and their liquidity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x22af...6f3b`](https://basescan.org/address/0x22af33fe49fd1fa80c7149773dde5890d3c76f3b) |
| **Network** | Base |
| **Price** | $0.0003882 |
| **24h Volume** | $631.3K |
| **Liquidity** | $1.94M |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 32.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1578 buys / 1625 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is BankrCoin a scam?

BankrCoin's status is not indicative of an outright scam based on available data. Its contract is verified, ownership is renounced, and no mint function exists, which are strong positive indicators against common scam tactics like malicious code or supply inflation. While liquidity is not locked, posing a risk, the low overall risk score of 18/100 suggests a generally positive security evaluation.

### Is BankrCoin safe to buy?

Investing in BankrCoin involves inherent risks. The primary concern is that liquidity is not locked, meaning the substantial liquidity pool could potentially be removed, leading to a drastic price drop. Additionally, the concentration of 33.2% of the supply among the top 10 holders presents a risk of market manipulation. Investors should weigh these factors against the low risk score and conduct personal due diligence.

### Has BankrCoin been audited?

BankrCoin's contract is verified, making its code publicly viewable for transparency. However, contract verification differs from a professional security audit, which involves a deep, independent review for vulnerabilities. The provided information does not confirm that BankrCoin has undergone such an audit. Investors should understand that verification alone does not guarantee security against all potential flaws.

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xaec085e5a5ce8d96a7bdd3eb3a62445d4f6ce703)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bankrcoin-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
