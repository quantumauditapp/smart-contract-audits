---
token: ESHARE
ticker: ESHARE
network: base
risk_score: 16
status: low
date: 2026-10-30
---

# ESHARE (ESHARE) — Smart Contract Security Analysis | Base

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/eshare-base)

---

## Audit Summary

The contract is a standard ERC-20 token with minting and burning capabilities. Ownership has been renounced, meaning the privileged administrative functions are now permanently disabled. The architecture follows standard OpenZeppelin patterns, ensuring high code reliability.

> **Final Recommendation:** The contract is secure and immutable due to the renouncement of ownership. No further action is required for the current implementation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20 and EIP-712 compliance. 7.1 Architecture is standard, 7.2 Code Security is high due to the use of established standards, and 7.3… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance factors are effectively neutralized by the renouncement of ownership. There is no active governance or economic control mechanism remaining. 7.8 Operations are… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy and does not implement any upgradeability patterns. The code is immutable, providing high security against unauthorized logic changes. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 68.5% |
| **Top-3 Unlocked** | ⚠️ 87.8% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.9% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a contract, 0xa958…4ba9 — holds 68.5% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 15% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 47.1% of supply. What remains: 21.9% in wallets, 25.2% in other contracts. 952 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as ESHARE (ESHARE), market cap $1M, rank #2863. 952 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $365K (DexScreener, all pools). 24h trading volume $122K (CoinGecko, all markets, daily snapshot). 24h trading volume $227K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 2% on sell. Market: $365K of DEX liquidity across 19 pools. Launch: 429 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb7c1...0871`](https://basescan.org/address/0xb7c10146ba1b618956a38605ab6496523d450871) |
| **Network** | Base |
| **Price** | $20.4600 |
| **24h Volume** | $59.0K |
| **Liquidity** | $53.5K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 47.1% of supply |
| **Buy / Sell Tax** | 0.0% / 2.0% |
| **24h Transactions** | 342 buys / 302 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x88026e8765f823c1a6dedc0d0fb1286e345ae3fb4214adb42ece9d6567d391dc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/eshare-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
