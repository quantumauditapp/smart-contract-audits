---
token: XTO 🔥
ticker: XTO
network: base
risk_score: 57
status: medium
date: 2026-10-24
---

# XTO 🔥 (XTO) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xto-base-57b5)

---

## Audit Summary

The audit evaluated the DERC20 smart contract on the Base network, focusing on standard compliance, security controls, and governance parameters. The contract integrates standard OpenZeppelin implementations including ERC20Votes, ERC20Permit, and vesting mechanics. However, administrative capabilities grant the contract owner control over pool trading states and inflationary mint rate adjustments.

> **Final Recommendation:** We recommend transferring contract ownership to a multi-signature wallet paired with a decentralized timelock controller. This structure ensures adequate community notice and review before privileged actions—specifically updateMintRate() or lockPool()—can take effect.

Additionally, consider implementing event emissions on all administrative state changes and formalizing transition paths to permanently renounce or irrevocably freeze the lockPool capability once initial liquidity has been stably established.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | Under 7.1 Architecture and 7.2 Code Security, the contract demonstrates robust adherence to OpenZeppelin ERC-20 standards, with clean implementation of EIP-712 permit signing and ERC-5805 voting… |
| **Governance / Economics** | 3/10 | High | In terms of 7.4 Economic mechanisms, the token features a hard-coded cap on annual inflation via MAX_YEARLY_MINT_RATE_WAD (2% per year), protecting holders from unbounded arbitrary dilution. Vesting… |
| **Upgrades** | 4/10 | Medium | Regarding 7.7 Upgrades, the contract is deployed as an immutable, non-proxy contract with no delegatecall routing or proxy upgrade patterns present. This design ensures the core bytecode and dispatch… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Privileged Supply Minting via Inflation Adjustment and Vesting  *(Severity: Medium · Status: Unresolved)*

The contract allows the owner to call updateMintRate(uint256) which automatically triggers mintInflation() when an active yearly cycle is in progress, expanding the total supply up to the 2% annual cap. While release() distributes already-allocated vested tokens, updateMintRate alters inflationary growth, diluting token holders.

**Recommendation:** Place updateMintRate behind a timelock and emit clear events when the mint rate is updated or tokens are minted. Document inflation scheduling transparently for token holders.


### `CP-05` — Administrative Transfer Restriction via Pool Lock Switch  *(Severity: Medium · Status: Unresolved)*

The owner has authority to invoke lockPool(address) and unlockPool(), toggling the boolean isPoolUnlocked and assigning the pool address. This switch decides whether transfers involving the pool are permitted or blocked, giving the owner unilateral power to freeze trading activity.

**Recommendation:** Restrict lockPool functionality to an initial launch window or implement a permanent pool unlocking mechanism that cannot be reversed by the owner once trading is initialized.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 10,026 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

10,026 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $146K (DexScreener, all pools). 24h trading volume $724K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $146K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf777...8c5b`](https://basescan.org/address/0xf77775a327762c94f2b444e57b8faee149f98c5b) |
| **Network** | Base |
| **Price** | $1.3300 |
| **24h Volume** | $724.2K |
| **Liquidity** | $146.3K |
| **Volume / Liquidity** | 5.0× |
| **Token Age** | 7h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3541 buys / 3287 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xcd7e811cf3e47ae05c98b41f518cbe91731f515dcfe024583cb4de8c5b28246d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xto-base-57b5)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
