---
token: Pons
ticker: PONS
network: ethereum
risk_score: 94
status: critical
date: 2026-08-30
---

# Pons (PONS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 94/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pons-eth)

---

## Audit Summary

The provided source code for the `TeamToken` contract is truncated, limiting a full review of its custom logic. Based on the available code, the contract implements a standard ERC20 token with `Ownable` access control and `SafeMath` for arithmetic operations. Key findings include centralized control over token supply via minting, a redundant address validation check, and the use of an older Solidity compiler version. The contract is not upgradeable, ensuring immutability but lacking flexibility for future enhancements or bug fixes.

> **Final Recommendation:** It is recommended to carefully consider the implications of centralized token minting and, if possible, implement a more decentralized or time-locked approach to supply management. Address the identified redundant code to optimize gas usage and consider upgrading to a more recent Solidity compiler version for enhanced security features. For future projects, evaluate the trade-offs between immutability and upgradeability based on the project's long-term vision and risk tolerance.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract leverages standard OpenZeppelin patterns for ERC20 and Ownable, enhancing code security (7.2 Code Security). The use of SafeMath effectively mitigates integer overflow/underflow… |
| **Governance / Economics** | 1/10 | High | The contract implements a centralized ownership model via the `Ownable` pattern (7.3 Access Control, 7.5 Governance). A significant economic risk (7.4 Economic) is the centralized control over token… |
| **Upgrades** | 2/10 | High | The contract is not designed with an upgrade mechanism (7.7 Upgrades), meaning its logic is immutable once deployed. This eliminates upgrade-specific risks such as proxy misconfigurations or logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `M-01` — Redundant Address Validation Check  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `checkIsAddressValid` modifier includes the check `require(ethAddress == address(ethAddress), '[Validation] invalid address');`. This condition is always true for a valid `address` type, making the check redundant (7.2 Code Security). It adds unnecessary gas cost to transactions that use this modifier without providing any additional security benefit.

**Recommendation:** Remove the redundant `require(ethAddress == address(ethAddress), '[Validation] invalid address');` line from the `checkIsAddressValid` modifier. The `require(ethAddress != address(0), '[Validation] invalid address');` check is sufficient for validating non-zero addresses.


### `M-02` — Centralized Control of Token Supply (Minting Capability)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract likely includes a minting function (indicated by the `TeamFinanceTokenMint` event) that is controlled by the contract owner. This allows the owner to arbitrarily increase the token supply. While a common design choice for some tokens, it introduces a significant centralization risk (7.3 Access Control, 7.4 Economic, 7.5 Governance) as the owner has unilateral power to devalue existing tokens, impacting the token's economy and trust in the system.

**Recommendation:** Evaluate whether such centralized control over token supply aligns with the project's long-term vision. If decentralization is a goal, consider implementing mechanisms such as a fixed supply, a capped minting limit, a multi-signature wallet for minting operations, or a time-locked minting schedule. Clearly communicate the minting policy to token holders.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — a single wallet (EOA) — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `L-01` — Older Solidity Compiler Version  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses `pragma solidity >=0.6.0 <0.8.0;` (specifically compiled with 0.6.12). While `SafeMath` is used to mitigate integer overflow/underflow, using an older compiler version means missing out on security improvements, bug fixes, and gas optimizations introduced in newer Solidity versions (e.g., 0.8.x which includes built-in overflow checks by default) (7.2 Code Security).

**Recommendation:** Consider upgrading the Solidity compiler version to a more recent stable release (e.g., 0.8.x). This would allow the contract to benefit from the latest security enhancements and optimizations. Ensure thorough testing if upgrading, as syntax changes or new features might require minor code adjustments.


### `I-01` — Immutability and Lack of Upgradeability  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is not designed with an upgrade mechanism (e.g., proxy pattern), meaning its logic is immutable once deployed (7.7 Upgrades). While this ensures that the contract's behavior cannot be changed post-deployment, it also means that any discovered bugs or desired feature enhancements would necessitate a new deployment and migration of assets, which can be a costly and disruptive operational challenge (7.8 Operations).

**Recommendation:** Understand the implications of immutability. For simple, well-audited contracts, immutability can be a strength. For complex protocols or those expecting future feature development, consider a well-tested upgradeable proxy pattern in future iterations, understanding the associated risks and operational overhead.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.2% of supply. What remains: 50.0% in wallets, 50.2% in other contracts.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $26.1M (DexScreener, all pools). 24h trading volume $8K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $26.1M of DEX liquidity across 1 pools. Launch: 18 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 18 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 18 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x07f5...2241`](https://etherscan.io/address/0x07f5b6823751c2e2cd4560f28af75ff887102241) |
| **Network** | Ethereum |
| **Price** | $0.05222 |
| **24h Volume** | $8.3K |
| **Liquidity** | $26.11M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 18d |
| **Top-10 Holders** | 100.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 64 buys / 44 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x4af9205b894ede647265880e4c2be442bc000855)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pons-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
