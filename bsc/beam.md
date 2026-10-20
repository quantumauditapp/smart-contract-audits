---
token: Beam
ticker: BEAM
network: bsc
risk_score: 55
status: medium
date: 2026-10-05
---

# Beam (BEAM) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/beam-bsc)

---

## Audit Summary

The BeamToken contract is an ERC-20 token implementation with standard functionalities and an AccessControl system. A key finding is the presence of a privileged minting function, which allows specific roles to increase the token supply, potentially diluting existing token holders.

> **Final Recommendation:** It is crucial to carefully manage the `MINTER_ROLE` associated with the `mint` function. This role should be assigned to a highly secure entity, such as a multi-signature wallet, to prevent unauthorized token creation and ensure community trust. Establish clear, transparent governance procedures for any minting events, including public announcements and, if possible, time-locks to allow for community review.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The BeamToken contract implements the ERC-20 standard, providing core functionalities like `transfer`, `balanceOf`, and `approve`. It also incorporates `AccessControlEnumerable` for managing… |
| **Governance / Economics** | 1/10 | High | The economic model of BeamToken includes a minting capability, allowing a designated `MINTER_ROLE` to increase the total supply via the `mint` function. This introduces a potential for token dilution… |
| **Upgrades** | 2/10 | High | The BeamToken contract is not implemented as an upgradeable proxy (7.1 Architecture). This means its logic is immutable once deployed, eliminating risks associated with upgradeability patterns such… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Privileged Minting Capability  *(Severity: Medium · Status: Unresolved)*

The `mint(address,uint256)` function allows an address with the `MINTER_ROLE` to create new tokens. This increases the total supply, which can dilute the value of existing tokens held by other users. This means that whoever controls the `MINTER_ROLE` can decide to create more tokens at any time, potentially reducing the value of tokens you hold.

**Recommendation:** Ensure that the `MINTER_ROLE` is assigned to a highly trusted entity or a multi-signature wallet. Implement robust governance procedures for any minting operations, including public announcements and time-locks if feasible, to provide transparency and community oversight.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xf92b…99cf — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 59.1% of supply. Of that, 3.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 55.1% in wallets, 0.0% in other contracts. 22,470 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Beam (BEAM), market cap $125M, rank #257. Traded on Binance, Coinbase. 22,470 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $348K (DexScreener, all pools). 24h trading volume $124.8M (CoinGecko, all markets, daily snapshot). 24h trading volume $336K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0442 on 2024-03-10; the price is now 94.5018% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $348K of DEX liquidity across 7 pools. Launch: 1074 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x62d0...bfce`](https://bscscan.com/address/0x62d0a8458ed7719fdaf978fe5929c6d342b0bfce) |
| **Network** | BNB Chain |
| **Price** | $0.002564 |
| **24h Volume** | $335.5K |
| **Liquidity** | $345.6K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 2y |
| **Top-10 Holders** | 59.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2904 buys / 2934 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x7a50f72f6091745d3cc3f1388b0ca5f2f14eff19)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/beam-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-05*
