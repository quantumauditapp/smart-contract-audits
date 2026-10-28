---
token: JAGENT
ticker: JAGENT
network: bsc
risk_score: 42
status: medium
date: 2026-10-28
---

# JAGENT (JAGENT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jagent-bsc)

---

## Audit Summary

The JagentTokenV2 contract is a standard ERC-20 token with added administrative controls for minting, burning, and transfer restrictions. The protocol relies on a centralized 'minter' role that holds significant power over token supply and holder liquidity. While the code follows standard OpenZeppelin patterns, the centralization of power represents a notable risk to token holders.

> **Final Recommendation:** It is recommended to transition the 'minter' role to a decentralized multi-signature wallet or a DAO-governed contract to mitigate the risks of single-point-of-failure. Implementing a timelock on sensitive administrative functions like 'setPoolBlocked' would provide transparency and protection to token holders against sudden policy changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin libraries for ERC-20 functionality, ensuring 7.1 Architecture and 7.2 Code Security standards are met. The implementation is clean and follows 7.8… |
| **Governance / Economics** | 4/10 | Medium | The protocol exhibits high centralization, violating 7.5 Governance best practices by concentrating power in a single minter address. The 7.4 Economic model allows for arbitrary supply inflation and… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, satisfying 7.7 Upgrades safety by design. The logic is immutable once deployed. No proxy patterns are utilized, eliminating risks associated with implementation… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 98.9% (≈ permanent lock) |
| **LP Locked** | 98.9% — Null Address |

## Security Findings

_🟡 3 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The 'minter' address has the authority to call the mint function, which increases the total supply of tokens. This allows the controller to dilute the value of existing holdings at any time.

**Recommendation:** Implement a hard cap on total supply or transition the minting authority to a decentralized governance mechanism.


### `CP-05` — Administrative Control Over Transfers  *(Severity: Medium · Status: Unresolved)*

The 'minter' can trigger the 'disableBlocks' function, which modifies the transfer logic. This grants the controller the ability to halt all token transfers or sales globally.

**Recommendation:** Remove the ability to globally disable transfers or implement a community-voted mechanism for such drastic actions.


### `CP-06` — Arbitrary Address Blacklisting  *(Severity: Medium · Status: Unresolved)*

The 'minter' can use 'setPoolBlocked' to prevent specific addresses from interacting with the token. This allows the controller to freeze individual user funds without due process.

**Recommendation:** Restrict the blacklisting functionality to only address malicious actors via a transparent, verifiable process, or remove the feature entirely.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 17.4% of supply. Of that, 4.4% burned, 6.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.5% in wallets, 0.6% in other contracts. 4,364 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,364 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

98.9% of the pool's LP is burned or time-locked. 98.9% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 1.1% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $197K (DexScreener, all pools). 24h trading volume $1.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 1% on buy, 2% on sell. Market: $197K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8e64...ae15`](https://bscscan.com/address/0x8e6442663a4f8c50b6132c68d42a30e7dfe4ae15) |
| **Network** | BNB Chain |
| **Price** | $0.00000143 |
| **24h Volume** | $1.77M |
| **Liquidity** | $197.3K |
| **Volume / Liquidity** | 9.0× |
| **Token Age** | 10h |
| **Top-10 Holders** | 17.4% of supply |
| **Buy / Sell Tax** | 1.0% / 2.0% |
| **24h Transactions** | 10236 buys / 11395 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xe6efcdef2b720d1eca2b69edb7ef357725680bea)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/jagent-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
