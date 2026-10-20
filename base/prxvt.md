---
token: PRXVT
ticker: PRXVT
network: base
risk_score: 73
status: high
date: 2026-10-06
---

# PRXVT (PRXVT) — Smart Contract Security Analysis | Base

> **Risk Score: 73/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/prxvt-base)

---

## Audit Summary

The AgentTokenV2 contract is an ERC-20 token deployed as an EIP-1167 minimal clone, meaning its logic is immutable and cannot be upgraded. The contract exhibits significant centralization, with an owner or factory address possessing extensive control over token parameters, transfer mechanisms, and even user balances. Key risks include the ability to directly manipulate token balances, blacklist users, modify transfer taxes, and redirect funds, posing a substantial risk to token holders.

> **Final Recommendation:** Token holders should be fully aware of the extensive control held by the `ownerorfactory` address, as this role can significantly impact their token holdings and the overall token economy. It is crucial for the project team to establish clear, transparent policies regarding the exercise of these privileged functions, especially those affecting user balances, transfer restrictions, and tax rates. Consider implementing a multi-signature wallet for the `ownerorfactory` role to enhance security and decentralize control, reducing the risk of a single point of failure or malicious action. Regular communication with the community about any changes made using these powerful functions is also recommended to maintain trust and transparency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The AgentTokenV2 contract implements the ERC-20 standard, providing basic token functionalities. It is deployed as an EIP-1167 minimal clone, ensuring its core logic is immutable and cannot be… |
| **Governance / Economics** | 1/10 | High | The economic model of AgentTokenV2 is highly centralized, with the `ownerorfactory` role having significant power over token economics and user interactions. This privileged address can set project… |
| **Upgrades** | 6/10 | Medium | The AgentTokenV2 contract is deployed as an EIP-1167 minimal clone, which means its implementation is fixed and cannot be upgraded (7.7 Upgrades). While this provides immutability and removes… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 94.1% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 3 High · 🟡 4 Medium · 🟢 2 Low · ⚪ 4 Informational_

### `CD-02` — Ignored Return Value for ERC-20 Transfers  *(Severity: High · Status: Unresolved)*

The `_addInitialLiquidity` function performs an ERC-20 token transfer but does not check the boolean return value of the `transfer` call. If the external token's `transfer` function fails (e.g., due to reentrancy guards or insufficient balance), the contract will not revert, potentially leading to an inconsistent state or loss of funds.

**Recommendation:** Token holders should be aware that if an internal token transfer fails within the `_addInitialLiquidity` function, the contract might not detect it. The project team should ensure that all external ERC-20 transfer calls check their return values to prevent silent failures and maintain contract integrity.


### `CP-02` — Privileged Address Can Manipulate Token Balances  *(Severity: High · Status: Unresolved)*

The `ownerorfactory` address has the ability to directly change token balances of any holder. Specifically, the `addInitialLiquidity(address)` function can write to other holders' balances, allowing the controller to burn or move tokens out of any targeted address without their consent.

**Recommendation:** Token holders should be aware that a privileged address can directly modify their token balances. The project team should ensure that the `ownerorfactory` role is secured with robust access controls, such as a multi-signature wallet, and that any use of this function is transparently communicated to the community.


### `CP-03` — Privileged Address Can Redirect Critical Contract Logic  *(Severity: High · Status: Unresolved)*

The `ownerorfactory` address can change the address of a critical external contract that influences how transfers behave. The `setProjectTaxRecipient` function allows the controller to replace the address that receives project taxes. Whoever controls this setting can redirect funds or potentially manipulate the flow of tokens.

**Recommendation:** Token holders should understand that a privileged address can change where tax funds are sent. The project team must ensure the `ownerorfactory` role is highly secured and that any changes to the `projectTaxRecipient` are publicly announced and justified.


### `CP-05` — Privileged Address Can Control Transfer Permissions  *(Severity: Medium · Status: Unresolved)*

The `ownerorfactory` address can enable or disable transfers for all token holders. Functions like `addInitialLiquidity` and `setProjectTaxRates` can change an on/off setting (`_autoSwapInProgress`, `_tokenHasTax`) that determines whether transfers or sales are allowed or refused, potentially freezing or unfreezing all token movements.

**Recommendation:** Token holders should be aware that a privileged address can unilaterally halt or resume all token transfers. The project team should implement clear policies and communication channels for any changes to transfer permissions, ensuring transparency and accountability.


### `CP-06` — Privileged Address Can Blacklist Individual Holders  *(Severity: Medium · Status: Unresolved)*

The `ownerorfactory` address can prevent specific token holders from moving or selling their tokens. The `addBlacklistAddress` and `removeBlacklistAddress` functions allow the controller to add or remove addresses from a blacklist, which is checked on every transfer. This means chosen holders can be arbitrarily blocked.

**Recommendation:** Token holders should know that a privileged address can prevent them from transferring their tokens. The project team should establish strict, transparent criteria for blacklisting and communicate any such actions clearly to the community, ideally with a mechanism for appeal.


### `CP-07` — Privileged Address Can Change Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The `ownerorfactory` address has the power to modify the fees applied to token transfers. Functions such as `setProjectTaxRates`, `addInitialLiquidity`, and `setSwapThresholdBasisPoints` allow the controller to change the percentage of tokens taken as a fee during transfers, directly impacting the net amount received by token holders.

**Recommendation:** Token holders should be aware that a privileged address can change transfer fees at any time. The project team should commit to transparent communication regarding any fee adjustments and consider implementing a community governance mechanism for such critical parameter changes.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a wallet, 0x5ec2…daa7 — holds 94.1% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CD-01` — Potential for Rounding Loss in Calculations  *(Severity: Low · Status: Unresolved)*

The `_autoSwap` function may experience rounding losses due to performing division before multiplication. This can lead to minor inaccuracies in calculations involving token amounts, potentially resulting in small discrepancies over time.

**Recommendation:** Token holders should be aware that minor rounding differences might occur in certain automated calculations. The project team should review the `_autoSwap` function to ensure calculations are performed in a multiplication-before-division order to minimize rounding errors.


### `CP-08` — Privileged Address Can Change Transfer Limits  *(Severity: Low · Status: Unresolved)*

The `ownerorfactory` address can modify numeric limits that affect token transfers. The `addInitialLiquidity` function can change settings like `fundedDate` and `projectTaxPendingSwap`, which might influence transfer thresholds or other operational limits checked during transactions.

**Recommendation:** Token holders should be aware that a privileged address can adjust certain transfer limits. The project team should clearly communicate any changes to these limits and their potential impact on token transactions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 81.4% of supply. Of that, 4.4% burned — not holders that can sell, so excluded from the concentration score. What remains: 15.8% in wallets, 61.3% in other contracts. The deployer/owner wallet itself holds 2.2%. 4,917 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as PRXVT by Virtuals (PRXVT), market cap $3M, rank #2098. 4,917 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $267K (DexScreener, all pools). 24h trading volume $66K (CoinGecko, all markets, daily snapshot). 24h trading volume $54K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $267K of DEX liquidity across 1 pools. Launch: 273 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4b5d...c5a9`](https://basescan.org/address/0x4b5d32a07b8d3ec5d6928caa30196f8dd6a7c5a9) |
| **Network** | Base |
| **Price** | $0.002933 |
| **24h Volume** | $54.0K |
| **Liquidity** | $267.4K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 81.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 173 buys / 55 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xf19135499ccc96622bc08dbd080aea66e9a08a44)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/prxvt-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
