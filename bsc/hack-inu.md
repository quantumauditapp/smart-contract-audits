---
token: Hack Inu
ticker: HI
network: bsc
risk_score: 50
status: medium
date: 2026-10-31
---

# Hack Inu (HI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hack-inu-bsc)

---

## Audit Summary

The contract is a standard ERC-20 token implemented as an EIP-1167 minimal clone. Ownership has been renounced on-chain, effectively locking the administrative functions and ensuring the current transfer logic remains immutable. The codebase is well-structured, though minor mathematical rounding issues and state shadowing were identified.

> **Final Recommendation:** Given that ownership is renounced, the contract is effectively immutable. Users should be aware that the current transfer logic is permanent and cannot be altered by any party.

For future deployments, ensure that all mathematical operations follow the 'multiply before divide' rule to maintain precision. Additionally, perform thorough static analysis to identify and resolve variable shadowing before finalizing production code.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract follows standard ERC-20 patterns with clean implementation logic. 7.1 Architecture: Uses EIP-1167 for gas-efficient deployment. 7.2 Code Security: Logic is generally sound, though… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic: The token functions as a standard asset without complex inflationary or deflationary mechanisms. 7.5 Governance: Ownership is renounced, meaning no central authority can influence token… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The contract is an EIP-1167 minimal clone, which is inherently immutable. 7.8 Operations: No upgrade paths exist, ensuring long-term consistency of the token logic. The implementation… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 64.4% |
| **Top-3 Unlocked** | ⚠️ 97.8% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-02` — State Variable Shadowing  *(Severity: High · Status: Unresolved)*

The contract contains instances where local variables shadow state variables, which can lead to unintended logic errors during state updates.

**Recommendation:** Rename local variables to ensure they do not conflict with existing state variable names.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 4 address(es) other than the owner/deployer. One of them — a wallet, 0xb6b0…a581 — holds 64.4% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CD-01` — Rounding Loss in Normalization  *(Severity: Low · Status: Unresolved)*

The 'normalizeAmount' function performs division before multiplication, which can lead to precision loss during token calculations.

**Recommendation:** Refactor the calculation to perform multiplication before division to maintain higher precision.


### `CP-05` — Dormant Administrative Transfer Controls  *(Severity: Informational · Status: Unresolved)*

The contract contains a 'setMode' function that allows an owner to toggle transfer rules. Because ownership has been renounced, this function is now permanently inaccessible, rendering the transfer logic immutable.

**Recommendation:** No action required as the renounced ownership provides a security guarantee against future changes.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 54.5% of supply. What remains: 8.6% in wallets, 45.8% in other contracts. 861 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

861 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $1.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu); launched on four.meme, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $11K of DEX liquidity across 2 pools. Launch: launched on four.meme, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1a70...4444`](https://bscscan.com/address/0x1a700335ece5c42834d6dd1f74204eec8e194444) |
| **Network** | BNB Chain |
| **Price** | $0.00001259 |
| **24h Volume** | $1.43M |
| **Liquidity** | $10.6K |
| **Volume / Liquidity** | 134.7× |
| **Token Age** | 16h |
| **Top-10 Holders** | 54.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11584 buys / 9431 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xf4da82c411c1e2038abd4fb71eb6dd8835581fa6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hack-inu-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
