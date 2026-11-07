---
token: Jztcoin
ticker: JZT
network: polygon
risk_score: 40
status: medium
date: 2026-11-07
---

# Jztcoin (JZT) — Smart Contract Security Analysis | Polygon

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jztcoin-poly)

---

## Audit Summary

PandaToken is a standard ERC-20 implementation deployed on Polygon. The contract logic is straightforward and adheres to standard token patterns, with no privileged administrative functions or complex upgradeability mechanisms. The primary concern identified is the accidental locking of native ETH sent to the contract address.

> **Final Recommendation:** The contract is secure for standard token operations. Users should be advised not to send native ETH directly to the contract address, as there is no mechanism to recover these funds.

No further code changes are strictly required for the token's core functionality. Future iterations could include a 'withdrawETH' function restricted to the owner if the contract is intended to handle native assets.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows standard ERC-20 patterns with 7.1 Architecture and 7.2 Code Security being robust. 7.3 Access Control is effectively non-existent as there are no privileged functions, which… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance factors are minimal as the contract is a simple utility token. There are no inflationary mechanisms or complex governance structures to manipulate. The lack of… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported, which provides immutability and security against proxy-based exploits. 7.8 Operations are straightforward, requiring no maintenance or state updates. The contract is… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 3 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 95.7% of supply. Of that, 80.0% burned, 0.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.5% in wallets, 0.1% in other contracts. The deployer/owner wallet itself holds 80.0%. A holder that also controls the contract can sell into its own liquidity. 1,939 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `CD-01` — Native ETH trapped in contract  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function that allows it to accept native ETH, but it lacks any function to withdraw or transfer these funds out of the contract. Any ETH sent to the contract address will be permanently locked.

**Recommendation:** If the contract is not intended to hold ETH, remove the receive function. If it is intended to hold ETH, implement a restricted function that allows the owner to withdraw the balance.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xba7d…b31b — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,939 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $462K (DexScreener, all pools). 24h trading volume $67K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $462K of DEX liquidity across 1 pools. Launch: 310 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc9be...83bc`](https://polygonscan.com/address/0xc9bef791701d868f34bd7f918f169af72ccb83bc) |
| **Network** | Polygon |
| **Price** | $0.1527 |
| **24h Volume** | $67.5K |
| **Liquidity** | $461.7K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 95.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 547 buys / 80 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0x2194131064d57d490ae2a1b087254eec02ea45f2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/jztcoin-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
