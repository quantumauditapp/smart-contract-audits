---
token: FLY
ticker: FLY
network: bsc
risk_score: 58
status: medium
date: 2026-10-31
---

# FLY (FLY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fly-bsc)

---

## Audit Summary

The GangMintToken is an ERC-20 compliant token with centralized administrative controls managed by a 'launchpad' address. The contract includes mechanisms for minting, reclaiming tokens, and setting liquidity pair rules. While the code follows standard ERC-20 patterns, the high level of centralization poses a risk to token holders if the launchpad address is compromised or acts maliciously.

> **Final Recommendation:** It is recommended to transition the 'launchpad' role to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single-point-of-failure. Additionally, implementing a timelock on sensitive functions like 'padMint' would provide transparency and protection for token holders against sudden supply changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard ERC-20 functionality with clean, modular code. 7.1 Architecture is straightforward, utilizing standard OpenZeppelin-like patterns. 7.2 Code Security is high, with no… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are centralized under the 'launchpad' role. This role has the power to mint tokens and manipulate transfer flows, which directly impacts token value. While… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable, which provides certainty for users regarding the token's behavior. 7.8 Operations are limited to the defined… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.6% (≈ permanent lock) |
| **LP Locked** | 99.6% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting and Reclaim Authority  *(Severity: Medium · Status: Unresolved)*

The 'launchpad' address has the authority to call 'padMint', 'reclaim', and 'pullFor'. These functions allow the controller to mint new tokens, increasing the total supply and diluting existing holders, or to force transfers of tokens from user wallets to the launchpad address.

**Recommendation:** Restrict the minting capability to a hard-coded maximum supply and consider removing the 'reclaim' and 'pullFor' functions if they are not strictly necessary for the protocol's long-term operation. If they must remain, ensure the 'launchpad' role is held by a secure, multi-signature contract.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 76.2% of supply. Of that, 54.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 21.6% in wallets, 0.0% in other contracts. 270 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

270 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.6% of the pool's LP is burned or time-locked. 99.6% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.4% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $27K (DexScreener, all pools). 24h trading volume $182K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 1% on buy, 2.01% on sell. Market: $27K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcd41...2c99`](https://bscscan.com/address/0xcd412f1a25875bbb03b56018905695d930542c99) |
| **Network** | BNB Chain |
| **Price** | $0.00001389 |
| **24h Volume** | $182.1K |
| **Liquidity** | $27.5K |
| **Volume / Liquidity** | 6.6× |
| **Token Age** | 15h |
| **Top-10 Holders** | 76.2% of supply |
| **Buy / Sell Tax** | 1.0% / 2.0% |
| **24h Transactions** | 1521 buys / 3260 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x77e7c52310822f7aaddbfcf2323793bc40342309)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fly-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
