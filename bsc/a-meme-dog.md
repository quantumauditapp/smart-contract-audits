---
token: A Meme Dog
ticker: AMD
network: bsc
risk_score: 82
status: high
date: 2026-11-04
---

# A Meme Dog (AMD) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 82/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/a-meme-dog-bsc)

---

## Audit Summary

The contract is a standard ERC-20 token with custom fee exclusion logic. Ownership has been renounced, rendering administrative functions dormant. However, critical vulnerabilities exist in the internal swap logic, specifically regarding token transfers and fund handling, which pose a risk to liquidity and user assets.

> **Final Recommendation:** The contract should be considered high-risk due to the identified vulnerabilities in the swap logic. Users should exercise extreme caution as the contract cannot be updated to fix these issues.

Developers should avoid using this contract in production environments. If a new version is deployed, ensure all external calls are checked for success and that arithmetic operations are performed in a way that preserves precision.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns but includes a flawed internal swap mechanism. 7.1 Architecture is standard, 7.2 Code Security is compromised by unchecked return values, and 7.3… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance are effectively static. Since ownership is renounced, no further changes to fee exclusions or token parameters can be made. The economic model is fixed, preventing… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are limited to standard token transfers. The contract is immutable, which provides security against malicious upgrades… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 98.0% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 1.5% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Unauthorized Token Withdrawal Risk  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function uses transferFrom in a way that could allow the contract to pull tokens from any address that has previously approved the contract, potentially draining user balances.

**Recommendation:** Restrict the scope of transferFrom calls to only interact with authorized liquidity pools or specific contract-owned addresses.


### `CD-04` — Unchecked Token Transfer Results  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function ignores the boolean return value of ERC-20 transfers, which may lead to silent failures where liquidity operations appear successful despite failing to move tokens.

**Recommendation:** Always verify the return value of transfer and transferFrom calls using a library like OpenZeppelin's SafeERC20.


### `CD-03` — Trapped ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function that accepts ETH, but there is no logic to withdraw or utilize these funds, causing them to be permanently locked in the contract.

**Recommendation:** Implement a withdrawal function restricted to a governance address or a mechanism to automatically swap and distribute trapped ETH.


### `CD-02` — Precision Loss via Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

In _executeSwapAndLiquify and _transfer, division is performed before multiplication, which causes rounding errors and loss of precision in fee calculations.

**Recommendation:** Perform all multiplications before divisions to maintain maximum precision during fee calculations.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 94.1% of supply. Of that, 94.0% burned — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 0.1% in other contracts. 15,208 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

15,208 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

98.0% of the pool's LP is burned or time-locked. 98.0% is locked in PinkLock02 until 24 Nov 2026 (19 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 2.0% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $230K (DexScreener, all pools). 24h trading volume $8.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (meme). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3.9% on buy, 4.14% on sell. Market: $230K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x545a...8ee9`](https://bscscan.com/address/0x545a12090624c95fb96ef9a4ce9b60e58be98ee9) |
| **Network** | BNB Chain |
| **Price** | $0.00656 |
| **24h Volume** | $8.75M |
| **Liquidity** | $229.9K |
| **Volume / Liquidity** | 38.1× |
| **Token Age** | 7h |
| **Top-10 Holders** | 94.1% of supply |
| **Buy / Sell Tax** | 3.9% / 4.1% |
| **24h Transactions** | 7688 buys / 1951 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x90e60ed576d78d46599ff0828f4d44da453648fd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/a-meme-dog-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
