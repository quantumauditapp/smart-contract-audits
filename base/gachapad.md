---
token: GachaPad
ticker: GACHA
network: base
risk_score: 75
status: high
date: 2026-10-11
---

# GachaPad (GACHA) — Smart Contract Security Analysis | Base

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gachapad-base)

---

## Audit Summary

The AgentTokenV4 contract is an ERC-20 token deployed as an EIP-1167 minimal clone, meaning its logic is fixed and not upgradeable. The contract exhibits a high degree of centralized control, with an owner/factory address possessing extensive privileges to modify core token parameters, including transfer rules, fees, and even individual token balances. The audit identified 8 findings, including 3 High, 3 Medium, and 2 Low severity issues, primarily related to these centralized controls and some technical implementation details.

> **Final Recommendation:** Token holders should be aware of the significant centralized control exercised by the `ownerorfactory` address over the AgentTokenV4 contract. It is recommended that the project team implement robust multi-signature controls for the `ownerorfactory` role to mitigate the risks associated with a single point of control. Additionally, a transparent process for any changes to critical parameters, such as tax rates or blacklisting, should be established and communicated to the community. Review and address the identified technical issues, particularly the direct balance manipulation and unchecked ERC-20 transfers, to enhance the overall security and reliability of the token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The AgentTokenV4 contract implements standard ERC-20 functionality. The code security analysis (7.2) revealed several issues, such as the `_addInitialLiquidity` function directly manipulating user… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) and governance (7.5) of the AgentTokenV4 are highly centralized, with significant power vested in the `ownerorfactory` address. This role can unilaterally change project tax… |
| **Upgrades** | 6/10 | Medium | The AgentTokenV4 contract is deployed as an EIP-1167 minimal clone, which means its implementation is fixed and cannot be upgraded. This architecture (7.1) eliminates risks associated with… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 83.2% |
| **Top-3 Unlocked** | ⚠️ 98.5% |

## Security Findings

_🟠 3 High · 🟡 4 Medium · 🟢 2 Low · ⚪ 5 Informational_

### `CD-02` — Token transfers might fail silently without warning  *(Severity: High · Status: Unresolved)*

The `_addInitialLiquidity` function performs an ERC-20 token transfer but does not check if the transfer was successful. If the underlying ERC-20 token's `transfer` function fails (e.g., due to reentrancy guards or insufficient allowance), the contract might not revert, leading to an inconsistent state where the tokens were not actually moved but the contract believes they were.

**Recommendation:** Token holders should be aware that internal token movements might not always succeed as expected. The project team should ensure that all external ERC-20 `transfer` calls are wrapped with `require(success, "Transfer failed");` or use OpenZeppelin's `SafeERC20` library to prevent silent failures and maintain contract integrity.


### `CP-02` — Owner/Factory can directly change anyone's token balance  *(Severity: High · Status: Unresolved)*

The `addInitialLiquidity` function, callable by the owner or factory, can directly modify the token balances of any address. This means the owner/factory could burn tokens from your wallet or move them to another address without your consent.

**Recommendation:** Token holders should understand that the owner/factory has the power to alter their token holdings. The project team should implement strong governance around the use of this function, ideally requiring multi-signature approval for any such operations, and limit its scope to only necessary initial setup.


### `CP-03` — Owner/Factory can redirect how token transfers work  *(Severity: High · Status: Unresolved)*

The `setTaxAccountingAdapter` function, controlled by the owner or factory, allows them to change an external contract that the token relies on for transfer logic. If this adapter contract is replaced with a malicious one, it could alter how your tokens are transferred, potentially leading to unexpected fees, freezes, or even loss of funds during transfers.

**Recommendation:** Token holders should be aware that the owner/factory can fundamentally change transfer behavior. The project team should ensure the `taxAccountingAdapter` is set to a trusted, audited contract and consider making this address immutable or subject to a time-locked governance process after initial setup.


### `CP-05` — Owner/Factory can enable or disable token transfers and sales  *(Severity: Medium · Status: Unresolved)*

Functions like `setProjectTaxRates`, `addInitialLiquidity`, and `distributeTaxTokens`, controlled by the owner or factory, can activate or deactivate certain transfer rules or tax mechanisms. This means the owner/factory could potentially stop or allow transfers and sales based on these settings, impacting your ability to move your tokens.

**Recommendation:** Token holders should be aware that transfer functionality can be altered. The project team should clearly communicate any changes to these settings and ensure they are used transparently and predictably.


### `CP-06` — Owner/Factory can blacklist specific token holders  *(Severity: Medium · Status: Unresolved)*

The `addBlacklistAddress` and `removeBlacklistAddress` functions, callable by the owner or factory, allow them to add or remove any address from a blacklist. If your address is blacklisted, you would be prevented from moving or selling your tokens.

**Recommendation:** Token holders should understand the risk of being blacklisted. The project team should establish clear, public criteria for blacklisting and implement a robust, transparent governance process for such actions, ideally involving community input or multi-signature approval.


### `CP-07` — Owner/Factory can change fees on token transfers  *(Severity: Medium · Status: Unresolved)*

Functions such as `setProjectTaxRates`, `addInitialLiquidity`, `distributeTaxTokens`, and `setSwapThresholdBasisPoints`, controlled by the owner or factory, can modify the fees applied to token transfers (buy and sell taxes). This means the owner/factory could increase or decrease the cost of transacting with the token at any time.

**Recommendation:** Token holders should be aware that transfer fees are subject to change by the owner/factory. The project team should clearly communicate any fee adjustments and provide a rationale for such changes to maintain trust.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 4 address(es) other than the owner/deployer. One of them — a wallet, 0xfe48…5312 — holds 83.2% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CD-01` — Potential for small rounding losses in tax calculations  *(Severity: Low · Status: Unresolved)*

The `_autoSwap` function, which handles tax calculations, performs division before multiplication. In Solidity, integer division truncates decimals, which can lead to minor rounding losses in calculations, potentially affecting the exact amount of tax collected or tokens swapped.

**Recommendation:** While often minor, this can lead to small discrepancies. The project team should consider reordering operations to perform multiplication before division where possible to minimize rounding errors and ensure precise calculations.


### `CP-08` — Owner/Factory can change limits on token transfers or wallet sizes  *(Severity: Low · Status: Unresolved)*

The `addInitialLiquidity` function, controlled by the owner or factory, can modify numeric limits that affect token transfers, such as thresholds or other parameters. This could potentially impact the maximum amount you can transfer in a single transaction or hold in your wallet.

**Recommendation:** Token holders should be aware that transfer limits can be adjusted. The project team should ensure that any changes to these limits are communicated transparently and do not unduly restrict legitimate token usage.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 81.4% of supply. What remains: 21.1% in wallets, 60.3% in other contracts. The deployer/owner wallet itself holds 14.2%. 480 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as GachaPad (GACHA). 480 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $59K (DexScreener, all pools). 24h trading volume $108K (CoinGecko, all markets, daily snapshot). 24h trading volume $156K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $59K of DEX liquidity across 4 pools. Launch: 3 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd5a0...3b84`](https://basescan.org/address/0xd5a09d20652b58872a2e0f302de6ad2326db3b84) |
| **Network** | Base |
| **Price** | $0.0001776 |
| **24h Volume** | $151.9K |
| **Liquidity** | $56.7K |
| **Volume / Liquidity** | 2.7× |
| **Token Age** | 3d |
| **Top-10 Holders** | 81.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 488 buys / 498 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x5fc1e90123785930ded018ab9da95e4411ef4144)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gachapad-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
