---
token: POPZERO
ticker: POPZERO
network: bsc
risk_score: 63
status: medium
date: 2026-11-02
---

# POPZERO (POPZERO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 63/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/popzero-bsc)

---

## Audit Summary

PopZeroToken is a standard ERC-20 token implementation on the BNB Smart Chain. The contract includes a minting mechanism restricted to a designated minter address, subject to a hardcoded maximum supply cap. The architecture is straightforward, utilizing OpenZeppelin-standard patterns for token management.

> **Final Recommendation:** The protocol should consider transitioning the 'minter' role to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single point of failure. Additionally, implementing a time-lock for any future changes to the minter address would provide transparency and security for token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract follows standard ERC-20 specifications, ensuring compatibility with existing DeFi ecosystems. 7.1 Architecture is clean and modular, while 7.2 Code Security benefits from the use of… |
| **Governance / Economics** | 1/10 | High | The economic model relies on a centralized minter role, which presents a trust requirement for token holders. 7.4 Economic stability is maintained by a hardcoded MAX_SUPPLY, preventing infinite… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, which provides immutability for users. 7.7 Upgrades are not applicable as the logic is fixed upon deployment. 7.8 Operations are simplified by the lack of proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.1% (≈ permanent lock) |
| **LP Locked** | 99.1% — Null Address |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows a single privileged address to create new tokens up to the maximum supply. This grants the controller the ability to dilute the value of existing holdings at their discretion.

**Recommendation:** Transition the minter role to a multi-signature wallet or a DAO-controlled contract to ensure that minting actions require community consensus or multi-party approval.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $402K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 37.2% of supply. Of that, 24.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 10.6% in wallets, 1.7% in other contracts. 1,467 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,467 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.1% of the pool's LP is burned or time-locked. 99.1% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.9% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 1% on buy, 3% on sell. Market: $9K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xeaf0...8f87`](https://bscscan.com/address/0xeaf035ef0a8038d7b558f3f872ed689aebc48f87) |
| **Network** | BNB Chain |
| **Price** | $0. |
| **24h Volume** | $402.4K |
| **Liquidity** | $8.6K |
| **Volume / Liquidity** | 46.5× |
| **Token Age** | 17h |
| **Top-10 Holders** | 37.2% of supply |
| **Buy / Sell Tax** | 1.0% / 3.0% |
| **24h Transactions** | 4462 buys / 5506 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xdc3062517b3021f2e7f3606955aa5b6da5d08f5c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/popzero-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
