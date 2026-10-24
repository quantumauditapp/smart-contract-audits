---
token: BNBCAT
ticker: BNBCAT
network: bsc
risk_score: 84
status: high
date: 2026-10-24
---

# BNBCAT (BNBCAT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bnbcat-bsc-c479)

---

## Audit Summary

The contract implements a standard ERC-20 token with custom fee logic. Ownership has been renounced, meaning privileged functions are now dormant. However, critical vulnerabilities exist in the internal swap logic that could lead to unauthorized token movement and loss of funds.

> **Final Recommendation:** The contract should be considered unsafe for deployment or use due to the critical vulnerability allowing unauthorized token transfers. Because ownership is renounced, these issues cannot be patched via contract updates.

Users should avoid interacting with this contract. If the token is intended for production, a redeployment with a corrected codebase that includes proper return value checks and secure arithmetic operations is required.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | The architecture follows standard ERC-20 patterns with additional fee-on-transfer logic. 7.1 Architecture is standard, but 7.2 Code Security is compromised by improper handling of external calls. 7.3… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance are effectively static. Since ownership is renounced, no further changes can be made to the fee structure or contract parameters. The economic model is fixed… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are limited to standard token transfers. The contract is immutable, providing certainty but also preventing the patching… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 97.2% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 2.8% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function allows the contract to move tokens from any address that has granted an allowance to the contract, potentially leading to unauthorized drainage of user funds.

**Recommendation:** Restrict the scope of token transfers to only those initiated by the contract's own balance or authorized liquidity pools.


### `CD-04` — Unchecked Transfer Return Values  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function fails to check the boolean return value of ERC-20 transfers, which can lead to silent failures where tokens are not moved as expected.

**Recommendation:** Always verify the return value of transfer and transferFrom calls, or use the SafeERC20 library from OpenZeppelin.


### `CD-03` — Locked ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract accepts ETH via receive() and deposit functions but lacks any mechanism to withdraw or transfer these funds, causing them to be permanently locked.

**Recommendation:** Implement a withdrawal function restricted to a secure address or ensure the contract does not accept ETH if it cannot be utilized.


### `CD-02` — Rounding Errors in Fee Calculation  *(Severity: Low · Status: Unresolved)*

The contract performs division before multiplication in _executeSwapAndLiquify and _transfer, which causes precision loss during fee calculations.

**Recommendation:** Rearrange arithmetic operations to perform multiplication before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.7% of supply. Of that, 90.0% burned, 0.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.4% in wallets, 0.0% in other contracts. 17,946 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

17,946 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

97.2% of the pool's LP is burned or time-locked. 97.2% is locked in PinkLock02 until 02 Nov 2026 (8 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 2.8% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $105K (DexScreener, all pools). 24h trading volume $6.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat). Tokenomics — Supply: mint capability could not be read. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4% on buy, 4.02% on sell. Market: $105K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5efb...f8a0`](https://bscscan.com/address/0x5efb2d65a1bd15bb85b2c4c86098c1c12ee5f8a0) |
| **Network** | BNB Chain |
| **Price** | $1.1500 |
| **24h Volume** | $6.06M |
| **Liquidity** | $105.1K |
| **Volume / Liquidity** | 57.7× |
| **Token Age** | 6h |
| **Top-10 Holders** | 90.7% of supply |
| **Buy / Sell Tax** | 4.0% / 4.0% |
| **24h Transactions** | 7729 buys / 1265 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x1397a524a9a33ed41b11aa4f43e460e91a0632f5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bnbcat-bsc-c479)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
