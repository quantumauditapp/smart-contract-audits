---
token: BNBCAT
ticker: BNBCAT
network: bsc
risk_score: 84
status: high
date: 2026-10-22
---

# BNBCAT (BNBCAT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bnbcat-bsc)

---

## Audit Summary

The contract implements a standard ERC-20 token with custom fee logic. While ownership has been renounced, preventing further administrative changes, the contract contains critical vulnerabilities in its internal swap and liquidity management logic. Specifically, the lack of return value checking and improper token handling in _executeSwapAndLiquify poses a significant risk to user funds.

> **Final Recommendation:** Immediate action is required to address the critical and high-severity findings. Since ownership is renounced, the contract cannot be patched; users should be advised of the risks associated with the liquidity management functions.

Future deployments should utilize OpenZeppelin's SafeERC20 library to handle token transfers and ensure all return values are validated. Avoid performing arithmetic operations that lead to precision loss and ensure all received ETH can be recovered by the contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | The architecture follows a standard ERC-20 implementation with additional fee-on-transfer logic. 7.1 Architecture is standard, but 7.2 Code Security is compromised by improper handling of external… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance risks are mitigated by the renounced ownership status. No further changes to fee structures or administrative roles can be made. The tokenomics are fixed, providing… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. 7.8 Operations are limited to standard token transfers. The contract is immutable. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 94.8% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 5.1% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Withdrawal Risk  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function uses transferFrom in a way that could allow the contract to pull tokens from any address that has previously approved the contract, potentially draining user balances.

**Recommendation:** Restrict the scope of transferFrom to only move tokens owned by the contract itself.


### `CD-04` — Unchecked Token Transfer Results  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function ignores the boolean return value of ERC-20 transfers, which can lead to silent failures where tokens are not actually moved but the contract state updates as if they were.

**Recommendation:** Use the SafeERC20 library to perform transfers and verify that the return value is true.


### `CD-03` — Locked ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract accepts ETH via receive() and deposit functions but lacks any mechanism to withdraw or transfer these funds out, effectively locking them permanently.

**Recommendation:** Implement a withdrawal function restricted to a secure address or a governance-controlled mechanism to recover trapped ETH.


### `CD-02` — Precision Loss via Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

In _executeSwapAndLiquify and _transfer, the code performs division before multiplication, which leads to rounding errors and potential loss of tokens during fee calculations.

**Recommendation:** Reorder operations to perform multiplication before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 88.1% of supply. Of that, 87.4% burned, 0.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.1% in wallets, 0.0% in other contracts. 47,560 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

47,560 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

94.8% of the pool's LP is burned or time-locked. 94.8% is locked in PinkLock02 until 16 Nov 2026 (24 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 5.2% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $273K (DexScreener, all pools). 24h trading volume $66.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat). Tokenomics — Supply: mint capability could not be read. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4.5% on buy, 4.56% on sell. Market: $273K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0fe7...d2cb`](https://bscscan.com/address/0x0fe7207ef2d695cce12ee6574aa1f78c2e9bd2cb) |
| **Network** | BNB Chain |
| **Price** | $4.0300 |
| **24h Volume** | $66.45M |
| **Liquidity** | $273.0K |
| **Volume / Liquidity** | 243.4× |
| **Token Age** | 11h |
| **Top-10 Holders** | 88.1% of supply |
| **Buy / Sell Tax** | 4.5% / 4.6% |
| **24h Transactions** | 19834 buys / 4599 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xed31cb4b0b6f9cf816d73cae501870fc2ab51688)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bnbcat-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
