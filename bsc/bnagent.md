---
token: BNAGENT
ticker: BNAGENT
network: bsc
risk_score: 56
status: medium
date: 2026-10-30
---

# BNAGENT (BNAGENT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bnagent-bsc)

---

## Audit Summary

BnagentToken is a standard ERC-20 token with additional administrative controls allowing the minter to manage supply and restrict transferability. The contract implements a centralized governance model where the minter role holds significant power over token liquidity and holder access. While the code follows standard OpenZeppelin patterns, the presence of blacklisting and transfer-blocking mechanisms introduces substantial centralization risk for token holders.

> **Final Recommendation:** To improve security, transition the minter role to a multi-signature wallet or a decentralized DAO governance contract to prevent single-point-of-failure risks. Implement a time-lock mechanism for any administrative actions that affect token supply or transferability to provide transparency and notice to the community.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin ERC-20 libraries, ensuring robust base functionality. 7.1 Architecture is straightforward, relying on a single-contract design. 7.2 Code Security is high… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are dominated by the minter role. The ability to mint tokens and block addresses creates a high risk of rug-pull or arbitrary fund freezing. There are no… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable, which provides certainty to users regarding the contract's behavior. 7.8 Operations are limited to the minter's… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.5% (≈ permanent lock) |
| **LP Locked** | 99.5% — Null Address |

## Security Findings

_🟡 3 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows the privileged minter to create new tokens at will. This can lead to significant dilution of existing token holders' value if the minter acts maliciously or their key is compromised.

**Recommendation:** Restrict the minting capability to a multi-signature wallet or implement a hard-coded supply cap that cannot be bypassed by the minter.


### `CP-05` — Arbitrary Transfer Blocking Switch  *(Severity: Medium · Status: Unresolved)*

The disableBlocks() function allows the minter to toggle a global switch that can halt all token transfers. This creates a risk where the minter can unilaterally freeze the entire market for the token.

**Recommendation:** Remove the global transfer-blocking functionality or implement a decentralized voting mechanism to trigger such a state change.


### `CP-06` — Blacklisting Capability  *(Severity: Medium · Status: Unresolved)*

The setPoolBlocked(address,bool) function allows the minter to blacklist specific addresses from transferring tokens. This gives the minter the power to censor individual users and prevent them from selling their holdings.

**Recommendation:** Limit the use of blacklisting to specific regulatory compliance scenarios and ensure the process is transparent and auditable.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 69.9% of supply. Of that, 28.2% burned, 33.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.1% in wallets, 3.1% in other contracts. 858 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

858 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.5% of the pool's LP is burned or time-locked. 99.5% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.5% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $14K (DexScreener, all pools). 24h trading volume $271K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 1% on buy, 2% on sell. Market: $14K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc7f9...c5fb`](https://bscscan.com/address/0xc7f95a3bff008053a4e2f235baf2f6d784e6c5fb) |
| **Network** | BNB Chain |
| **Price** | $0.00000002 |
| **24h Volume** | $271.5K |
| **Liquidity** | $13.8K |
| **Volume / Liquidity** | 19.6× |
| **Token Age** | 18h |
| **Top-10 Holders** | 69.9% of supply |
| **Buy / Sell Tax** | 1.0% / 2.0% |
| **24h Transactions** | 2663 buys / 4219 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x7d4fde617a4f5d83fd8a354672558d9b9cd5aa6f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bnagent-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
