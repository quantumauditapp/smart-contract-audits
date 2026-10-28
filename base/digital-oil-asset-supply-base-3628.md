---
token: Digital Oil Asset Supply
ticker: DOAS
network: base
risk_score: 56
status: medium
date: 2026-10-28
---

# Digital Oil Asset Supply (DOAS) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/digital-oil-asset-supply-base-3628)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation rates and pool access. While the code follows standard OpenZeppelin patterns, the high level of administrative control over token supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** It is recommended to implement a timelock contract for all administrative functions, specifically those impacting supply (updateMintRate) and transferability (lockPool/unlockPool). This would provide token holders with a window of notice before significant changes occur.

Additionally, consider transitioning ownership to a decentralized governance model or a multi-signature wallet to mitigate the single point of failure inherent in the current 'Ownable' implementation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, Votes, and Permitting. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard, battle-tested… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner has unilateral authority to mint tokens and halt transfers via pool locking. While 7.6 External dependencies are minimal… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable, ensuring that the current administrative functions cannot be altered or removed without a new deployment. This… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply at their discretion, which directly dilutes the value of existing token holdings.

**Recommendation:** Implement a timelock for minting operations or cap the total supply to prevent arbitrary inflation.


### `CP-05` — Administrative Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch using the lockPool and unlockPool functions. This allows the owner to unilaterally disable or enable token transfers, effectively freezing user funds or restricting market liquidity.

**Recommendation:** Remove the ability to pause transfers or move this functionality to a decentralized governance vote.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 11 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

11 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $101K (DexScreener, all pools). 24h trading volume $402K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $101K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0015...faf9`](https://basescan.org/address/0x001563da203a35849b77f4fb71d90f58be0afaf9) |
| **Network** | Base |
| **Price** | $0.2188 |
| **24h Volume** | $402.0K |
| **Liquidity** | $100.9K |
| **Volume / Liquidity** | 4.0× |
| **Token Age** | 13h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1565 buys / 1043 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xceeff328829c0a78785f6e4c44d9761bdcc6b25dfd2e748f8fe86749ca578c0e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/digital-oil-asset-supply-base-3628)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
