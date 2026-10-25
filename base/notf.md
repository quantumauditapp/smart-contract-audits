---
token: NOTF
ticker: NOTF
network: base
risk_score: 57
status: medium
date: 2026-10-25
---

# NOTF (NOTF) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/notf-base)

---

## Audit Summary

The DERC20 contract implements a standard ERC-20 token integrated with OpenZeppelin voting, permit, and vesting extensions on Base. The implementation follows modern Solidity patterns with strict bounds on inflation minting, but retains centralized privileged controls over liquidity pool interactions and token supply expansion.

> **Final Recommendation:** The protocol should transition administrative authority from a single owner to a timelocked multi-signature wallet or decentralized governance structure to mitigate single point of failure risks. Restricting discretionary pool locking and enforcing explicit event emissions on all administrative state changes will significantly enhance transparency.

Additionally, consider implementing immutable bounds or programmatic schedules for pool locking mechanisms to guarantee unhindered liquidity and trading freedom for all market participants.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | Regarding 7.1 Architecture and 7.2 Code Security, the contract demonstrates robust structure by inheriting established OpenZeppelin contracts such as ERC20Votes, ERC20Permit, and Ownable using… |
| **Governance / Economics** | 3/10 | High | Under 7.4 Economic considerations, the contract provides strong economic guardrails by capping the annual inflation rate with MAX_YEARLY_MINT_RATE_WAD in updateMintRate to prevent arbitrary… |
| **Upgrades** | 4/10 | Medium | Under 7.7 Upgrades, the contract is deployed as an immutable non-proxy implementation on Base, eliminating common proxy storage collision and implementation hijacking risks. The codebase benefits… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Privileged Token Minting Dilutes Existing Holders  *(Severity: Medium · Status: Unresolved)*

The contract owner possesses administrative authority to increase the circulating token supply through the updateMintRate(uint256) and release() functions. When updateMintRate is called, it triggers mintInflation() if an active yearly period has elapsed, diluting the relative balance and voting weight of existing token holders.

**Recommendation:** Enforce transparent minting schedules governed by a timelock or decentralized governance vote rather than direct owner invocation, and consider lowering or permanently capping maximum emission bounds.


### `CP-05` — Owner Controlled Switch Can Restrict Pool Transfers  *(Severity: Medium · Status: Unresolved)*

The contract owner controls liquidity access via lockPool(address) and unlockPool(), which alter the isPoolUnlocked flag and modify the registered pool address. This switch can be utilized to block or restrict transfers involving designated decentralized exchange liquidity pools at the owner's discretion.

**Recommendation:** Remove the arbitrary pool locking switch after initial launch or enforce an irreversible one-way unlock to ensure permanent and unhampered trading access for token holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 10,005 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

10,005 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $173K (DexScreener, all pools). 24h trading volume $364K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $173K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe2cc...541d`](https://basescan.org/address/0xe2cc332525834e89649278e55c3e5ad63b14541d) |
| **Network** | Base |
| **Price** | $0.4438 |
| **24h Volume** | $364.1K |
| **Liquidity** | $173.1K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 6h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2850 buys / 2800 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xdcbe65169f8d8ef7d58b1891d5e3ecd02579d9c85cbe6364c03105de103c5023)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/notf-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
