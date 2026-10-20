---
token: Catecoin
ticker: CATE
network: bsc
risk_score: 74
status: high
date: 2026-10-19
---

# Catecoin (CATE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 74/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/catecoin-bsc)

---

## Audit Summary

The audited Token contract on BSC implements standard ERC-20 tokenomics with built-in liquidity fee handling and fee exclusions. Contract ownership has been verified as renounced on-chain, rendering all owner-restricted administration functions permanently dormant. However, critical vulnerabilities exist in internal automated swap logic where unauthorized token movements can occur, alongside unhandled transfer returns and trapped native assets.

> **Final Recommendation:** Users should exercise extreme caution when granting allowances to this contract. Because _executeSwapAndLiquify can pull tokens from arbitrary addresses holding allowances, users must strictly avoid approving tokens to the contract beyond exact transaction requirements or consider revoking approvals entirely.

For future iterations, the development team must ensure that liquidity management routines only transfer tokens directly owned by the contract rather than relying on caller-defined addresses. Additionally, safe transfer wrappers such as SafeERC20 should be integrated, rounding operations sequenced after multiplications, and dedicated withdrawal methods implemented for any native currency received.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Under 7.1 Architecture, the token relies on standard ERC-20 foundations and structured modular inheritance from OpenZeppelin Context and Ownable. Regarding 7.2 Code Security, fundamental validation… |
| **Governance / Economics** | 6/10 | Medium | Under 7.5 Governance, the contract eliminates administrative rug-pull vectors because contract ownership is renounced and owner functions like setExclusionFromFee are rendered dormant. In 7.4… |
| **Upgrades** | 6/10 | Medium | In 7.7 Upgrades, the contract is deployed as an immutable non-proxy instance, ensuring that bytecode cannot be altered or hijacked post-deployment. Regarding 7.8 Operations, routine user transactions… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 97.2% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 1.8% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — Arbitrary Token Pull in Swap Routine  *(Severity: Critical · Status: Unresolved)*

The internal function _executeSwapAndLiquify executes transferFrom using an address that the caller can manipulate or that draws from third-party balances. Anyone who has approved the contract can have their tokens transferred without their direct authorization.

**Recommendation:** Refactor _executeSwapAndLiquify to only transfer tokens held directly in the contract's own balance using address(this) rather than pulling from external user balances.


### `CD-04` — Unchecked Return Value in External Token Transfers  *(Severity: High · Status: Unresolved)*

The function _executeSwapAndLiquify performs ERC-20 token transfers without checking the returned boolean status. If a transfer fails silently, the contract continues execution under the false assumption that funds were moved.

**Recommendation:** Use OpenZeppelin's SafeERC20 safeTransfer and safeTransferFrom functions to verify successful transfer execution and revert on failure.


### `CD-03` — Permanent Locking of Received Native Assets  *(Severity: Medium · Status: Unresolved)*

The contract implements a receive function that accepts native BNB payments but lacks any withdrawal function or outgoing transfer mechanism, causing any sent funds to be permanently trapped.

**Recommendation:** Remove the receive function if native assets are not required, or implement an explicit, protected sweep function to route received native currency to a secure receiver.


### `CD-02` — Precision Loss Due to Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

In _executeSwapAndLiquify and _transfer, mathematical calculations perform division before multiplication, leading to avoidable rounding loss and truncated fee amounts during token processing.

**Recommendation:** Reorder mathematical expressions to perform all multiplication steps prior to division, preserving precision throughout fee and liquidity calculations.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 94.3% of supply. Of that, 94.0% burned, 0.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 0.0% in other contracts. 43,339 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

43,339 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

97.2% of the pool's LP is burned or time-locked. 97.3% is locked in PinkLock02 until 19 Nov 2026 (30 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. 2.7% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $163K (DexScreener, all pools). 24h trading volume $9.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3.9% on buy, 3.94% on sell. Market: $163K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5b9e...f1e2`](https://bscscan.com/address/0x5b9ea2cf91592b0e87b9772dc0a693fb8654f1e2) |
| **Network** | BNB Chain |
| **Price** | $0.03214 |
| **24h Volume** | $9.38M |
| **Liquidity** | $162.8K |
| **Volume / Liquidity** | 57.6× |
| **Token Age** | 20h |
| **Top-10 Holders** | 94.3% of supply |
| **Buy / Sell Tax** | 3.9% / 3.9% |
| **24h Transactions** | 17292 buys / 4906 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xa8724ec16c35d5cd5b51e2751866620cd654870a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/catecoin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
