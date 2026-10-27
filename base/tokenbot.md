---
token: tokenbot
ticker: CLANKER
network: base
risk_score: 7
status: low
date: 2026-08-31
---

# tokenbot (CLANKER) — Smart Contract Security Analysis | Base

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tokenbot-base)

---

## Audit Summary

The SocialDexDeployer contract facilitates the creation of new ERC20 tokens, initializes Uniswap V3 liquidity pools, and manages associated fees. The audit identified several high-severity issues, including inconsistent fee calculations and a denial-of-service vulnerability in the salt generation mechanism. Medium-severity findings include an arbitrary address requirement for token deployment and a theoretical integer overflow risk. The contract relies on external Uniswap V3 components and a custom locker factory, whose security is assumed. Centralized control by the owner is present for key parameters.

> **Final Recommendation:** It is strongly recommended to address the high-severity issues related to inconsistent fee calculations and the denial-of-service vulnerability in `generateSalt` immediately. The arbitrary `token < weth` requirement should be re-evaluated for its necessity and potential negative impacts. All identified medium and low-severity findings, including the theoretical integer overflow and the typo in supply validation, should be resolved to enhance the contract's robustness and security. Furthermore, consider implementing a multi-signature wallet for owner functions to mitigate centralization risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract demonstrates a clear architecture for token deployment and liquidity management (7.1 Architecture), leveraging standard ERC20 and Uniswap V3 interfaces. However, several technical… |
| **Governance / Economics** | 6/10 | Medium | The economic model presents a high risk due to inconsistent fee calculations (7.4 Economic). The `protocolCut` is applied as a permille, while `lpFeesCut` is passed directly, creating potential for… |
| **Upgrades** | 9/10 | Low | The SocialDexDeployer contract is not designed as an upgradeable proxy (7.7 Upgrades). It is deployed as a standard, immutable contract. Therefore, there are no upgrade-specific vulnerabilities or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 88.0% |
| **Top-3 Unlocked** | ⚠️ 99.6% |

## Security Findings

_🟡 4 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `M-01` — Arbitrary `token < weth` Requirement for Token Deployment  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `deployToken` function includes a `require(address(token) < weth, "Invalid salt");` check. This condition forces the newly deployed token's address (determined by `create2` with a salt) to be numerically smaller than the `weth` address. The purpose of this arbitrary restriction is unclear and introduces an unnecessary constraint on token deployment. It can significantly limit the available `create2` salts, making it harder and potentially more gas-intensive to find a valid salt, especially if `weth` is a low address or if the address space below `weth` becomes crowded.

**Recommendation:** Clarify the rationale behind the `token < weth` requirement. If it serves no critical security or functional purpose, it should be removed to allow for more flexible token deployment and reduce potential friction for users. If it is deemed necessary, document its purpose and consider alternative, less restrictive mechanisms.


### `M-02` — Potential Integer Overflow in `protocolFees` Calculation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The calculation `uint256 protocolFees = (msg.value * protocolCut) / 1000;` could theoretically lead to an integer overflow. While Solidity 0.8.0+ prevents overflows by default, the intermediate product `msg.value * protocolCut` could exceed `type(uint256).max` if `msg.value` is extremely large (e.g., close to `type(uint256).max / protocolCut`). Although `protocolCut` is a `uint8` (max 255) and `msg.value` is typically limited by the amount of ETH sent in a transaction, this remains a theoretical vulnerability for extremely high `msg.value` scenarios.

**Recommendation:** While the practical likelihood is low, consider reordering the multiplication and division to reduce the chance of overflow, for example, `(msg.value / 1000) * protocolCut` if `msg.value` is guaranteed to be a multiple of 1000, or use a safe math library if `protocolCut` could be larger. Alternatively, ensure `protocolCut` is always small enough that `type(uint256).max / protocolCut` is greater than any practically expected `msg.value`.


### `M-03` — Inconsistent Fee Calculation and Unused Variable  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract exhibits inconsistent logic for calculating and applying fees. The `protocolCut` is used in the calculation `(msg.value * protocolCut) / 1000`, implying it's a permille (parts per thousand). In contrast, `lpFeesCut` is passed directly to `liquidityLocker.deploy` without scaling, suggesting it might be interpreted as a percentage (0-100) or another unit by the external locker contract. This inconsistency can lead to misconfiguration, incorrect fee distribution, and unexpected economic outcomes. Additionally, the `taxRate` variable is declared and has an owner-only update function (`updateTaxRate`) but is ne

**Recommendation:** Standardize all fee parameters to use a consistent unit (e.g., basis points or permille) and ensure all calculations reflect this. Clearly document the expected units for all fee-related variables. Either implement the intended use for `taxRate` or remove it to avoid confusion and reduce contract complexity.


### `M-04` — Denial of Service via `generateSalt` Function  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `generateSalt` function contains an infinite loop (`for (uint256 i; ; i++)`) designed to find a suitable `salt` value. This loop is constrained by two conditions: `token < weth` and `token.code.length == 0`. The `token < weth` condition is arbitrary and significantly restricts the address space for valid tokens. If a suitable salt that satisfies both conditions is difficult to find (e.g., if `weth` is a very low address, or if many addresses below `weth` are already occupied), the loop could iterate excessively, causing the transaction to run out of gas. This leads to a denial of service for users attempting to use

**Recommendation:** Re-evaluate the necessity of the `token < weth` condition. If it's not critical, remove it. If it is, consider implementing a more efficient salt generation mechanism or providing a maximum iteration limit to prevent indefinite loops and potential gas exhaustion. Users should be aware of the potential for high gas costs when using this function.


### `L-01` — Typo in Supply Validation  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `deployToken` function includes the validation `require(_supply >= _supply, "Invalid supply amount");`. This condition will always evaluate to `true` and therefore does not effectively validate the `_supply` parameter. It fails to prevent the deployment of tokens with a zero supply, which could lead to unexpected behavior or issues with subsequent liquidity provisioning.

**Recommendation:** Change the validation to `require(_supply > 0, "Supply must be greater than zero");` to ensure that tokens are deployed with a positive initial supply.


### `L-02` — Centralized Control by Owner  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `SocialDexDeployer` contract inherits `Ownable`, granting the deployer (owner) significant control over critical parameters. The owner can update `taxCollector`, `liquidityLocker`, `defaultLockingPeriod`, `lpFeesCut`, and `taxRate`. This centralization introduces a single point of failure and a high degree of trust in the owner's actions, which could pose a risk if the owner's key is compromised or acts maliciously.

**Recommendation:** For enhanced security and decentralization, consider implementing a multi-signature wallet for ownership, or introducing a time-lock mechanism for sensitive parameter updates. This would add a layer of security and transparency to critical administrative actions.


### `I-01` — Misleading Function Name  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The function `updateProtocolFees(uint8 newFee)` is named in a way that suggests it updates a general 'protocol fees' variable. However, its implementation `lpFeesCut = newFee;` reveals that it specifically updates the `lpFeesCut` variable. This naming inconsistency can lead to confusion for auditors, developers, and users, potentially resulting in misconfiguration.

**Recommendation:** Rename the function to `updateLpFeesCut(uint8 newFee)` to accurately reflect its purpose and improve code clarity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1bc0...1bcb`](https://basescan.org/address/0x1bc0c42215582d5a085795f4badbac3ff36d1bcb) |
| **Network** | Base |
| **Price** | $12.5200 |
| **24h Volume** | $29.7K |
| **Liquidity** | $1.43M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 60.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 172 buys / 169 sells |

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

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xc1a6fbedae68e1472dbb91fe29b51f7a0bd44f97)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tokenbot-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
