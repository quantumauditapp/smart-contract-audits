---
token: BNBHolder
ticker: BNBH
network: bsc
risk_score: 57
status: medium
date: 2026-11-02
---

# BNBHolder (BNBH) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bnbholder-bsc)

---

## Audit Summary

The BNBHolderToken is an ERC-20 token implementation featuring centralized control mechanisms. While the core token logic follows standard patterns, the contract grants a 'minter' role significant power to manipulate supply, block transfers, and restrict liquidity. The protocol relies on trust in the minter address, as there are no time-locks or multi-signature requirements for these privileged actions.

> **Final Recommendation:** Token holders should be aware that the minter address possesses absolute control over token liquidity and supply. It is recommended to transition the minter role to a multi-signature wallet or a decentralized governance contract to mitigate the risk of single-point-of-failure or malicious intent.

Furthermore, implementing a time-lock on sensitive functions like 'setPoolBlocked' or 'mint' would provide transparency and allow the community to react to significant changes in token economics.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin-like ERC-20 logic for transfers and allowances. 7.1 Architecture is straightforward, relying on a single-owner initialization pattern. 7.2 Code Security is… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance risks are elevated due to the centralized nature of the minter role. The minter can unilaterally dilute holders via minting or prevent trading via block-listing. These… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable post-deployment. 7.8 Operations are limited to the functions defined in the source code. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.7% (≈ permanent lock) |
| **LP Locked** | 99.7% — Null Address |

## Security Findings

_🟡 3 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The 'mint' function allows the designated minter to create new tokens at will, which can lead to the dilution of existing token holders' value.

**Recommendation:** Restrict the minting capability to a capped supply or require a multi-signature approval process for any new issuance.


### `CP-05` — Centralized Transfer Control  *(Severity: Medium · Status: Unresolved)*

The 'disableBlocks' function allows the minter to globally halt or enable transfers, effectively giving them the power to freeze the entire market for this token.

**Recommendation:** Remove the global transfer switch or implement a decentralized governance mechanism to trigger such a state change.


### `CP-06` — Address-Level Blacklisting  *(Severity: Medium · Status: Unresolved)*

The 'setPoolBlocked' function allows the minter to prevent specific addresses from transferring tokens, which can be used to censor individual users.

**Recommendation:** Limit the use of blacklisting to specific, transparent compliance scenarios or remove the functionality entirely to ensure censorship resistance.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 64.7% of supply. Of that, 43.1% burned, 13.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.1% in wallets, 4.0% in other contracts. 930 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

930 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.7% of the pool's LP is burned or time-locked. 99.7% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.3% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $212K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $18K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe08d...b360`](https://bscscan.com/address/0xe08dab5507df2f65c46641c5fecc6f3514c2b360) |
| **Network** | BNB Chain |
| **Price** | $0.00000006 |
| **24h Volume** | $211.5K |
| **Liquidity** | $18.2K |
| **Volume / Liquidity** | 11.6× |
| **Token Age** | 18h |
| **Top-10 Holders** | 64.7% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 2414 buys / 3105 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xf9da2fbb830452c0ebb71e428bb1ed914770acba)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bnbholder-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
