---
token: LITY
ticker: LITY
network: bsc
risk_score: 0
status: low
date: 2026-10-30
---

# LITY (LITY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lity-bsc)

---

## Audit Summary

LaunchToken is a standard ERC-20 token implementation on the Binance Smart Chain. The contract includes fee-on-transfer mechanics controlled by an owner. Ownership has been successfully renounced, effectively locking the administrative functions and ensuring the current fee structure is immutable. 7.1 Architecture: Standard ERC-20 with fee logic. 7.2 Code Security: Clean implementation using OpenZeppelin standards. 7.3 Access Control: Ownership renounced, no active privileged roles. 7.4 Economic: Fees are fixed and immutable. 7.5 Governance: N/A. 7.6 External: No external dependencies. 7.7 Upgrades: Not upgradeable. 7.8 Operations: No operational risks identified.

> **Final Recommendation:** The contract is secure due to the renunciation of ownership, which prevents any further administrative changes to the fee structure. No further action is required as the code is immutable and functions as intended.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a standard ERC-20 implementation with robust logic for fee handling. The code is concise and follows established security patterns for token contracts. The use of OpenZeppelin's… |
| **Governance / Economics** | 10/10 | Low | The economic model is defined by fixed buy and sell fees. Since ownership is renounced, these parameters cannot be manipulated by any party. This provides high predictability for token holders… |
| **Upgrades** | 10/10 | Low | The contract is not upgradeable and does not utilize proxy patterns. The logic is immutable, eliminating risks associated with contract upgrades or logic changes. This architecture provides maximum… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 0.0% |

## Security Findings

_⚪ 7 Informational_

### `CP-07` — Immutable Fee Structure  *(Severity: Informational · Status: Unresolved)*

The contract includes a setFees function that allows the owner to modify transaction fees. Because ownership has been renounced, this function is now dormant and cannot be called by anyone, making the current fee settings permanent.

**Recommendation:** No action required as the renunciation of ownership is a security best practice for fixed-supply or immutable tokens.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 77.0% of supply. Of that, 51.7% locked, 4.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 6.5% in wallets, 14.2% in other contracts. 833 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

833 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 27 May 2027 (208 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $833K (DexScreener, all pools). 24h trading volume $355K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $833K of DEX liquidity across 1 pools. Launch: 3 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd705...49c8`](https://bscscan.com/address/0xd7057e7c56b9c2d5f0a3e639d07610db31c949c8) |
| **Network** | BNB Chain |
| **Price** | $0.004465 |
| **24h Volume** | $354.6K |
| **Liquidity** | $832.6K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 3d |
| **Top-10 Holders** | 77.0% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 1054 buys / 219 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x91727e4485542612e9ed4293d1021414dbf5e588)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lity-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
