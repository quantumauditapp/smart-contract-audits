---
token: SnowBall Agent
ticker: SNOWBALL
network: bsc
risk_score: 72
status: high
date: 2026-11-02
---

# SnowBall Agent (SNOWBALL) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/snowball-agent-bsc)

---

## Audit Summary

SnowballToken is a standard ERC-20 implementation with additional minting and burning capabilities restricted to a minter role. The architecture is straightforward and follows standard OpenZeppelin patterns. The primary risk involves the centralization of the minter role, which has the authority to increase total supply up to a defined cap.

> **Final Recommendation:** It is recommended to transition the minter role to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single point of failure. Additionally, implementing a timelock for any significant minting operations would provide transparency and allow the community to react to supply changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes standard OpenZeppelin ERC-20 logic, ensuring robust compliance with token standards (7.1 Architecture, 7.2 Code Security). The transfer path is clean and free of complex… |
| **Governance / Economics** | 3/10 | High | The economic model relies on a centralized minter role, which introduces trust assumptions (7.4 Economic, 7.5 Governance). While a MAX_SUPPLY cap is implemented to limit inflation, the minter can… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, eliminating risks associated with proxy patterns (7.7 Upgrades). The logic is immutable, providing certainty to token holders regarding the contract's behavior. No… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 98.4% (≈ permanent lock) |
| **LP Locked** | 98.4% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows a privileged minter to create new tokens, which dilutes the value of existing holdings. This function is restricted to the minter role, but there are no constraints on how often or to whom these tokens are minted, other than the global MAX_SUPPLY cap.

**Recommendation:** Consider replacing the single minter address with a multi-signature wallet or a DAO-controlled contract to require consensus before minting new tokens. Alternatively, document the minting schedule clearly for token holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 46.5% of supply. Of that, 30.0% burned, 10.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 6.4% in wallets, 0.0% in other contracts. 6,647 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

6,647 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

98.4% of the pool's LP is burned or time-locked. 98.4% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 1.6% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $47K (DexScreener, all pools). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $47K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x79b5...61fb`](https://bscscan.com/address/0x79b5d86089a29a65fac3278572f00c8fadc361fb) |
| **Network** | BNB Chain |
| **Price** | $0.00000026 |
| **24h Volume** | $1.07M |
| **Liquidity** | $46.5K |
| **Volume / Liquidity** | 22.9× |
| **Token Age** | 23h |
| **Top-10 Holders** | 46.5% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 8877 buys / 7867 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x8c18cf56c5cce496d88752528aca95a099a94bc1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/snowball-agent-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
