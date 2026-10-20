---
token: Trump
ticker: TRUMP
network: bsc
risk_score: 81
status: high
date: 2026-10-20
---

# Trump (TRUMP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 81/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trump-bsc-2b69)

---

## Audit Summary

The contract is a standard ERC-20 token with custom fee-exclusion logic. Ownership has been renounced, meaning privileged functions like setTrailblazers are now permanently disabled. The audit identified critical vulnerabilities regarding token movement and ETH handling that pose significant risks to users.

> **Final Recommendation:** The contract is currently in a high-risk state due to the critical vulnerability in the liquidity execution logic. Since ownership is renounced, these issues cannot be patched by the original developers.

Users should exercise extreme caution. The inability to recover ETH sent to the contract and the potential for unauthorized token movement via the swap function represent significant security hazards that cannot be mitigated without a migration to a new, audited contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns with an added fee-exclusion mechanism. 7.1 Architecture is standard, 7.2 Code Security is compromised by unchecked return values, and 7.3 Access… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance are currently static as ownership is renounced. No further changes to fee structures or tokenomics can be made by the original deployer. The economic model relies on… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as this is a non-proxy contract. The logic is immutable, ensuring no future backdoors can be introduced via upgrade patterns. 7.8 Operations are limited to standard… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 97.3% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 2.7% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function allows the contract to move tokens from any address that has previously approved the contract, potentially leading to unauthorized drainage of user funds.

**Recommendation:** Restrict the _executeSwapAndLiquify function to only move tokens owned by the contract itself rather than arbitrary addresses.


### `CD-04` — Ignored Transfer Return Values  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function fails to check the boolean return value of ERC-20 transfers, which can lead to silent failures where tokens are not moved but the contract state assumes success.

**Recommendation:** Always verify the return value of transfer calls or use OpenZeppelin's SafeERC20 library.


### `CD-03` — Locked ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract accepts ETH via the receive function but lacks any mechanism to withdraw or utilize these funds, effectively locking any ETH sent to the contract address permanently.

**Recommendation:** Implement a withdrawal function restricted to a secure multi-sig or governance contract to recover trapped ETH.


### `CD-02` — Rounding Errors in Math  *(Severity: Low · Status: Unresolved)*

The contract performs division before multiplication in _executeSwapAndLiquify and _transfer, which causes precision loss and potential rounding errors in fee calculations.

**Recommendation:** Reorder mathematical operations to perform multiplication before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.4% of supply. Of that, 90.0% burned, 0.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.1% in wallets, 0.0% in other contracts. 17,044 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

17,044 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

97.3% of the pool's LP is burned or time-locked. 97.3% is locked in PinkLock02 until 01 Nov 2026 (11 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 2.7% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $113K (DexScreener, all pools). 24h trading volume $4.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4% on buy, 4.02% on sell. Market: $113K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1a55...38a7`](https://bscscan.com/address/0x1a55683068d46de29f49775961a8147aed9c38a7) |
| **Network** | BNB Chain |
| **Price** | $1.3400 |
| **24h Volume** | $4.27M |
| **Liquidity** | $113.3K |
| **Volume / Liquidity** | 37.7× |
| **Token Age** | 10h |
| **Top-10 Holders** | 90.4% of supply |
| **Buy / Sell Tax** | 4.0% / 4.0% |
| **24h Transactions** | 6804 buys / 1697 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xebf43eff3640ceb06d760a2c506b793a5879f451)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trump-bsc-2b69)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
