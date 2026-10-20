---
token: BagsPay
ticker: BAGSPAY
network: solana
risk_score: 0
status: low
date: 2026-10-02
---

# BagsPay (BAGSPAY) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bagspay-sol)

---

## Audit Summary

This audit of the BagsPay SPL token mint identifies a low-severity risk related to mutable metadata, allowing the token's name, symbol, or image to be changed post-launch. Key authorities, including mint and freeze, have been revoked, indicating a fixed supply and unfreezable accounts. Holder concentration data was unavailable, and liquidity is moderate with a significant portion locked.

> **Final Recommendation:** Holders should verify the current token metadata (name, symbol, image) against their expectations, as it can be changed by an authority. Monitor the token's official channels for any announcements regarding metadata updates. While mint and freeze authorities are revoked, the lack of holder concentration data means monitoring liquidity movements and trading patterns remains prudent.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The BagsPay token operates on the standard spl-token program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no holder accounts can be… |
| **Governance / Economics** | 10/10 | Low | The token has a total DEX liquidity of $113,420, with 95.5% of this liquidity locked for good in the pool program, enhancing stability. The remaining 4.4% is held by three other addresses. The… |
| **Upgrades** | 10/10 | Low | The mint and freeze authorities are permanently revoked, preventing any future changes to supply or account freezing capabilities. However, the token's metadata is mutable, meaning its name, symbol… |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token's metadata is mutable, as indicated by 'metadata_mutable: True'. This means that the token's name, symbol, or image can be changed post-launch by the controlling authority.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding. Be aware that the token's identity elements could be altered in the future.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

95.5% of the pool's LP is burned or time-locked. 95.5% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. 4.4% is held, unlocked, by 3 address(es) other than the pool's creator. This assessment covers the main pool, which holds 87% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $131K (DexScreener, all pools). 24h trading volume $583K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $131K of DEX liquidity across 11 pools. Launch: 3 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`H8WTvo...BAGS`](https://solscan.io/account/H8WTvo3ZXSYHJAcYqzCforbG8coR1FDAX2kHFfqHBAGS) |
| **Network** | Solana |
| **Price** | $0.0006334 |
| **24h Volume** | $494.2K |
| **Liquidity** | $113.6K |
| **Volume / Liquidity** | 4.4× |
| **Token Age** | 3d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3361 buys / 2469 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/dxsbgayrefnfxgu9tec17n4usq5jjy4zf9djt7rblrgf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bagspay-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-02*
