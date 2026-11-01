---
token: CENSUS
ticker: CENSUS
network: bsc
risk_score: 63
status: medium
date: 2026-11-01
---

# CENSUS (CENSUS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 63/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/census-bsc)

---

## Audit Summary

CensusToken is a standard ERC-20 implementation with additional administrative controls. The contract includes centralized functions that allow a privileged 'minter' to mint tokens, burn tokens from arbitrary addresses, and block specific addresses from interacting with the token. While the code follows standard ERC-20 patterns, the centralization of power poses significant risks to token holders.

> **Final Recommendation:** It is strongly recommended to transition the 'minter' role to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single point of failure. Implementing a time-lock on sensitive administrative functions like balance manipulation would provide users with notice before significant changes occur.

Users should be aware that the token is not fully decentralized and that the minter holds the power to freeze assets or alter the total supply at any time. Transparency regarding the identity and security practices of the minter is essential for long-term trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin-style ERC-20 logic for core functionality. 7.1 Architecture is straightforward, relying on a single-contract design. 7.2 Code Security is high due to the… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are dominated by the minter role. The minter has unilateral control over supply (minting) and individual user balances (burning). This creates a high trust… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are limited to the defined administrative functions. The lack of upgradeability ensures the contract logic remains… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 98.2% (≈ permanent lock) |
| **LP Locked** | 98.2% — Null Address |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 6 Informational_

### `CP-02` — Unauthorized Balance Manipulation  *(Severity: High · Status: Unresolved)*

The burnFromMinter(address,uint256) function allows the minter to remove tokens from any user's wallet without their consent.

**Recommendation:** Remove the ability to burn tokens from arbitrary addresses or require user approval for such actions.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows the privileged minter to create new tokens, which dilutes the value of existing holdings.

**Recommendation:** Restrict minting to a multi-signature wallet or implement a hard-coded supply cap that cannot be bypassed.


### `CP-06` — Arbitrary Address Blocking  *(Severity: Medium · Status: Unresolved)*

The setPoolBlocked function allows the minter to prevent specific addresses from transferring their tokens, effectively freezing their assets.

**Recommendation:** Implement a transparent, community-voted process for blacklisting or remove the functionality entirely.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 62.3% of supply. Of that, 53.1% burned, 5.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 3.2% in wallets, 1.0% in other contracts. 1,502 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,502 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

98.2% of the pool's LP is burned or time-locked. 98.3% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 1.7% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $36K (DexScreener, all pools). 24h trading volume $917K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 1% on buy, 2% on sell. Market: $36K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfc96...5708`](https://bscscan.com/address/0xfc96737a40dbf169782e60539b82d4ee17f25708) |
| **Network** | BNB Chain |
| **Price** | $0.00000033 |
| **24h Volume** | $917.5K |
| **Liquidity** | $35.5K |
| **Volume / Liquidity** | 25.8× |
| **Token Age** | 1d |
| **Top-10 Holders** | 62.3% of supply |
| **Buy / Sell Tax** | 1.0% / 2.0% |
| **24h Transactions** | 7842 buys / 6836 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x4752e61ca6c065a55eaa4fced1fcd52133f014c0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/census-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
