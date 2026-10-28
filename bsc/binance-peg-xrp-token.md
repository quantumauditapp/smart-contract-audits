---
token: Binance-Peg XRP Token
ticker: XRP
network: bsc
risk_score: 100
status: critical
date: 2026-10-28
---

# Binance-Peg XRP Token (XRP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/binance-peg-xrp-token-bsc)

---

## Audit Summary

The contract is a standard ERC-20 token with custom fee exclusion logic. Ownership has been renounced, rendering administrative functions like setExclusionFromFee permanently inaccessible. The contract contains critical logic flaws regarding token transfers and fund management that pose significant risks to users and liquidity.

> **Final Recommendation:** The contract should be considered high-risk due to the inability to recover trapped funds and the failure to validate token transfer results. Users should exercise extreme caution as the current implementation of _executeSwapAndLiquify is prone to failure and potential fund loss.

Since ownership is renounced, the contract cannot be patched. Future deployments should implement proper return value checks for all ERC-20 interactions and include emergency withdrawal functions for any native currency sent to the contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The architecture follows standard ERC-20 patterns but includes flawed internal swap logic. 7.1 Architecture is standard, 7.2 Code Security is compromised by unchecked return values, and 7.3 Access… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance risks are mitigated by the renounced ownership, preventing further changes to fee structures. However, the inability to withdraw trapped ETH represents a permanent… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. 7.8 Operations are static and immutable. The lack of upgradeability ensures the current logic, including its flaws, is permanent. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 96.7% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 3.3% |

## Security Findings

_🔴 2 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `CD-01` — Unauthorized Token Movement  *(Severity: Critical · Status: Unresolved)*

The _executeSwapAndLiquify function uses transferFrom to move tokens from arbitrary addresses, which could allow the contract to drain tokens from users who have approved the contract.

**Recommendation:** Restrict the source of transferFrom to only the contract's own balance or authorized liquidity pools.


### `QA-IDENTITY` — Imitation of XRP (XRP)  *(Severity: Critical · Status: Acknowledged)*

Presents itself as XRP (XRP), but the established XRP token on bsc is Binance-Peg XRP, 0x1d2f0da169ceb9fc7b3144628db156f3f6c60dbe (CoinGecko). Holders who think they own the real asset own this contract instead; it has none of the real asset's backing, liquidity or redemption.

**Recommendation:** Do not buy, hold or accept this token as the asset it names. Verify any token address against the issuer's official site.


### `CD-04` — Ignored Transfer Results  *(Severity: High · Status: Unresolved)*

The _executeSwapAndLiquify function performs token transfers without checking the boolean return value, which can lead to silent failures where the contract assumes a transfer succeeded when it actually reverted.

**Recommendation:** Always wrap ERC-20 transfers in a require statement or use OpenZeppelin's SafeERC20 library.


### `CD-03` — Trapped Native Currency  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function that allows it to accept ETH/BNB, but it lacks any function to withdraw or transfer these funds out, causing them to be permanently locked.

**Recommendation:** Implement an emergency withdrawal function that allows a designated address or the community to recover trapped native currency.


### `CD-02` — Rounding Errors in Math  *(Severity: Low · Status: Unresolved)*

The contract performs division before multiplication in _executeSwapAndLiquify and _transfer, which leads to precision loss and inaccurate fee calculations.

**Recommendation:** Reorder arithmetic operations to perform multiplication before division to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.3% of supply. Of that, 90.0% burned, 0.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.1% in wallets, 0.0% in other contracts. 17,262 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

96.7% of the pool's LP is burned or time-locked. 96.7% is locked in PinkLock02 until 07 Nov 2026 (9 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. 3.3% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $272K (DexScreener, all pools). 24h trading volume $6.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Imitation of XRP (XRP)  *(Severity: Informational · Status: Acknowledged)*

A token presenting itself under the name or ticker of an established asset without being that asset's contract. Its only reason to borrow that identity is to be mistaken for it. Scored as an imitation (see the identity finding). Basis: behaves as: project token. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 4% on buy, 4.11% on sell. Market: $272K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Do not treat this token as the asset it names. Use only the official contract address published by that asset's issuer.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa64a...0168`](https://bscscan.com/address/0xa64a35f0760eebd7d50261fab9c05bd953200168) |
| **Network** | BNB Chain |
| **Price** | $0.7422 |
| **24h Volume** | $6.22M |
| **Liquidity** | $271.8K |
| **Volume / Liquidity** | 22.9× |
| **Token Age** | 5h |
| **Top-10 Holders** | 90.3% of supply |
| **Buy / Sell Tax** | 4.0% / 4.1% |
| **24h Transactions** | 8600 buys / 1155 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x1cf8987274d7a708c69092c807aafdff4c0c0e04)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/binance-peg-xrp-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
