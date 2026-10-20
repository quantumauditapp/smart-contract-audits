---
token: Black Shiba
ticker: MANYU
network: bsc
risk_score: 45
status: medium
date: 2026-10-18
---

# Black Shiba (MANYU) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/black-shiba-bsc)

---

## Audit Summary

The CheeseTaxTokenV2 contract is an ERC-20 token implementation with a specific role, 'taxprocessor', capable of pausing transfers. The contract also has a mechanism to receive Ether (ETH) but lacks a function to withdraw it, leading to potential loss of funds. Ownership of the contract has been renounced, making owner-restricted functions dormant.

> **Final Recommendation:** It is recommended to review the necessity and control mechanism of the `taxprocessor` role, especially its ability to pause transfers. Consider implementing a multi-signature wallet or a time-lock for critical functions like `setSwapping` to enhance security and decentralization. Additionally, address the issue of unwithdrawable ETH by either removing the `receive` function if ETH is not intended to be held, or by implementing a secure withdrawal mechanism.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The CheeseTaxTokenV2 contract implements the ERC-20 standard, providing essential token functionalities (7.1 Architecture). The code includes a `setSwapping` function, controlled by the… |
| **Governance / Economics** | 8/10 | Low | The contract's ownership has been renounced on-chain, meaning functions restricted to the owner (e.g., `transferOwnership`) are no longer callable (7.3 Access Control). However, a specific… |
| **Upgrades** | 8/10 | Low | The CheeseTaxTokenV2 contract is not implemented as an upgradeable proxy, meaning its logic cannot be changed after deployment (7.7 Upgrades). This eliminates upgrade-related risks but also prevents… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 82.3% |
| **LP Locked** | 82.3% — Null Address |

## Security Findings

_🟡 3 Medium · ⚪ 5 Informational_

### `CD-01` — Stuck Ether (ETH)  *(Severity: Medium · Status: Unresolved)*

The contract includes a `receive` function, allowing it to accept Ether (ETH). However, there are no corresponding functions to withdraw any received ETH, meaning any Ether sent to this contract will be permanently locked and inaccessible.

**Recommendation:** If the contract is not intended to hold ETH, consider removing the `receive` function to prevent accidental deposits. If ETH is intended to be held, implement a secure withdrawal mechanism, preferably controlled by a multi-signature wallet.


### `CP-05` — Privileged Address Can Halt Transfers  *(Severity: Medium · Status: Unresolved)*

The `taxprocessor` address has the ability to call the `setSwapping` function, which controls a switch (`_swapping`) that determines if token transfers are allowed. If `_swapping` is set to `false`, all transfers of CheeseTaxTokenV2 may be prevented, potentially impacting liquidity and trading.

**Recommendation:** Token holders should be aware that the `taxprocessor` can unilaterally stop all token transfers. Consider implementing a multi-signature wallet for the `taxprocessor` role or a time-lock mechanism for such critical functions to add a layer of security and transparency.


### `QA-LIQUIDITY` — Liquidity only partly locked or burned  *(Severity: Medium · Status: Acknowledged)*

82.3% of the pool's LP is burned or time-locked. 82.3% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 17.7% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 22.9% of supply. Of that, 16.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 6.3% in wallets, 0.0% in other contracts. 967 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

967 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $42K (DexScreener, all pools). 24h trading volume $400K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (shib). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $42K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8a64...6666`](https://bscscan.com/address/0x8a64dd261385ccaa79c4f2dc941f2e2683186666) |
| **Network** | BNB Chain |
| **Price** | $0.0001239 |
| **24h Volume** | $400.0K |
| **Liquidity** | $42.2K |
| **Volume / Liquidity** | 9.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | 22.9% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 2404 buys / 2193 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x7f1aa5830253ee670bfa31435ef611fabea7c9ce)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/black-shiba-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-18*
