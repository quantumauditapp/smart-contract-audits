---
token: Zcash Token
ticker: ZEC
network: bsc
risk_score: 99
status: critical
date: 2026-10-21
---

# Zcash Token (ZEC) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 99/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zcash-token-bsc-708e)

---

## Audit Summary

The contract is a standard ERC-20 token with custom fee exclusion logic. Ownership has been renounced, meaning privileged functions are now permanently disabled. However, the contract contains critical logic flaws in its internal swap and liquidity management functions that pose significant risks to token holders.

> **Final Recommendation:** The contract is currently unsafe for use due to critical vulnerabilities in the internal swap logic. Since ownership is renounced, the contract cannot be patched or upgraded to fix these issues.

Users should avoid interacting with any functions that trigger the internal swap mechanism. Given the immutability of the contract, the current deployment should be considered deprecated and replaced with a new version that includes proper return value checks and secure arithmetic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | The architecture follows standard ERC-20 patterns with added fee-on-transfer logic. 7.1 Architecture is simple but flawed in its liquidity execution. 7.2 Code Security is compromised by unchecked… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance are effectively neutralized as the contract owner has renounced control. No further changes to fee exclusions or ownership can be made. The economic model relies on… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as this is a standard non-proxy contract. The logic is immutable. 7.8 Operations are limited to standard token transfers and the broken internal swap mechanism. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 97.4% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 1.8% |

## Security Findings

_🔴 2 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `CD-01` — Unauthorized Token Withdrawal  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function allows the contract to move tokens from any address that has approved the contract, potentially draining user balances.

**Recommendation:** Restrict the function to only move tokens owned by the contract itself.


### `QA-IDENTITY` — Imitation of Zcash (ZEC)  *(Severity: Critical · Status: Acknowledged)*

Presents itself as Zcash (ZEC), but CoinGecko lists no Zcash contract on bsc at all (CoinGecko). Holders who think they own the real asset own this contract instead; it has none of the real asset's backing, liquidity or redemption.

**Recommendation:** Do not buy, hold or accept this token as the asset it names. Verify any token address against the issuer's official site.


### `CD-04` — Unchecked Token Transfer Result  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function ignores the return value of ERC-20 transfers, which may fail silently and lead to inconsistent state.

**Recommendation:** Use OpenZeppelin's SafeERC20 library to ensure all transfers are successful.


### `CD-03` — Stuck ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract can receive ETH via the receive function but lacks any mechanism to withdraw or utilize these funds, causing them to be permanently locked.

**Recommendation:** Implement a withdrawal function restricted to a secure address or remove the receive function.


### `CD-02` — Rounding Loss via Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

Calculations in _executeSwapAndLiquify and _transfer perform division before multiplication, leading to precision loss.

**Recommendation:** Perform all multiplications before divisions to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 66.6% of supply. Of that, 65.9% burned, 0.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 0.3% in other contracts. 19,248 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

97.4% of the pool's LP is burned or time-locked. 97.4% is locked in PinkLock02 until 11 Nov 2026 (20 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 2.6% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $390K (DexScreener, all pools). 24h trading volume $10.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Imitation of Zcash (ZEC)  *(Severity: Informational · Status: Acknowledged)*

A token presenting itself under the name or ticker of an established asset without being that asset's contract. Its only reason to borrow that identity is to be mistaken for it. Scored as an imitation (see the identity finding). Basis: behaves as: project token. Tokenomics — Supply: mint capability could not be read. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3.9% on buy, 3.9% on sell. Market: $390K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Do not treat this token as the asset it names. Use only the official contract address published by that asset's issuer.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x77a7...aca3`](https://bscscan.com/address/0x77a78c698b8b42d1d956d373b37be45d5fdfaca3) |
| **Network** | BNB Chain |
| **Price** | $14.7900 |
| **24h Volume** | $10.08M |
| **Liquidity** | $389.6K |
| **Volume / Liquidity** | 25.9× |
| **Token Age** | 8h |
| **Top-10 Holders** | 66.6% of supply |
| **Buy / Sell Tax** | 3.9% / 3.9% |
| **24h Transactions** | 8868 buys / 3190 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xc444906d45f27b17b3af5621062f6e8d02e59bd2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zcash-token-bsc-708e)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
