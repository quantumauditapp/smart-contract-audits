---
token: MGO
ticker: MGO
network: bsc
risk_score: 42
status: medium
date: 2026-10-20
---

# MGO (MGO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mgo-bsc)

---

## Audit Summary

The MGO token is a standard ERC-20 implementation with added administrative controls. While the core token logic follows standard patterns, the contract includes highly privileged functions that allow the owner to unilaterally burn user balances. This creates a significant centralization risk for token holders.

> **Final Recommendation:** The protocol should consider implementing a multi-signature wallet or a time-lock mechanism for the privileged 'destroyFreezeFunds' function to mitigate the risk of unilateral asset seizure. Transparency regarding the intended use of these administrative powers is recommended to maintain user trust.

Furthermore, consider renouncing ownership if the administrative features are no longer required after the initial deployment phase. This would permanently remove the centralization risk and align the contract with decentralized standards.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin libraries for ERC-20 functionality, ensuring 7.1 Architecture and 7.2 Code Security standards are met. 7.3 Access Control is implemented via Ownable… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner has the ability to modify user balances and freeze accounts via the 'destroyFreezeFunds' function. This represents a… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, which provides 7.7 Upgrades stability. 7.8 Operations are straightforward as there are no complex vault or staking mechanisms. The lack of proxy patterns prevents… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 80.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 4 Informational_

### `CP-02` — Privileged access to burn user balances  *(Severity: High · Status: Unresolved)*

The 'destroyFreezeFunds' function allows the contract owner to burn the entire balance of any address that has been flagged with a specific role. This gives the owner the power to unilaterally remove tokens from any user's wallet.

**Recommendation:** Remove the ability for the owner to burn user balances, or implement a multi-signature requirement and a time-lock delay to ensure that such actions are transparent and subject to community oversight.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x6eaa…5dbb — holds 80.8% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.7% of supply. Of that, 78.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 10.9% in wallets, 9.9% in other contracts. 155,693 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Mango Network (MGO), market cap $9M, rank #1283. 155,693 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $391K (DexScreener, all pools). 24h trading volume $641K (CoinGecko, all markets, daily snapshot). 24h trading volume $110K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-5 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $391K of DEX liquidity across 1 pools. Launch: 483 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5e0d...8eb1`](https://bscscan.com/address/0x5e0d6791edbeeba6a14d1d38e2b8233257118eb1) |
| **Network** | BNB Chain |
| **Price** | $0.005638 |
| **24h Volume** | $110.3K |
| **Liquidity** | $391.2K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 99.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 212 buys / 229 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x83bd3ceadc3c19af0264157f4b70f0402c9bb3a8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mgo-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
