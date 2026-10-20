---
token: PLAYZAP
ticker: PZP
network: bsc
risk_score: 50
status: medium
date: 2026-10-11
---

# PLAYZAP (PZP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/playzap-bsc)

---

## Audit Summary

The PZP contract is an ERC-20 token implementation with additional administrative functions for managing roles and facilitating fund transfers. The audit found no critical or high-severity vulnerabilities in the provided code. However, the contract exhibits a high degree of centralization, with significant control over contract funds vested in specific administrative roles. This centralization introduces operational and governance risks that warrant careful management.

> **Final Recommendation:** To mitigate the risks associated with high centralization, it is strongly recommended to implement a multi-signature wallet for controlling the `owner` and `admin` roles. This would require multiple trusted parties to approve critical operations, significantly reducing the risk of a single point of failure or a compromised private key leading to unauthorized fund movements. Additionally, review the necessity of such broad fund-moving powers for the `HasRole` addresses and consider implementing time locks or additional checks for high-value transactions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The PZP contract implements standard ERC-20 functionality and incorporates `ReentrancyGuard` for all privileged fund-out functions, enhancing code security (7.2 Code Security). Access control is… |
| **Governance / Economics** | 1/10 | High | The contract's economic security is highly dependent on the integrity of the `owner` and `admin` keys. The `admin` can manage who has the `HasRole`, and these `HasRole` addresses possess the… |
| **Upgrades** | 6/10 | Medium | The PZP contract is not designed with upgradeability features, as indicated by `is_proxy: false`. This means the contract's logic is immutable once deployed, eliminating risks associated with proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x6af0…6cc2 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 76.9% of supply. Of that, 1.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 54.4% in wallets, 20.7% in other contracts. 3,949 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as PlayZap (PZP), rank #3393. 3,949 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $34K (DexScreener, all pools). 24h trading volume $666K (CoinGecko, all markets, daily snapshot). 24h trading volume $106K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.57 on 2023-11-11; the price is now 98.967% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $34K of DEX liquidity across 1 pools. Launch: 710 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdce4...9612`](https://bscscan.com/address/0xdce40c14d5956f8b8ba912402ba73b4d4d599612) |
| **Network** | BNB Chain |
| **Price** | $0.006574 |
| **24h Volume** | $106.2K |
| **Liquidity** | $33.8K |
| **Volume / Liquidity** | 3.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 76.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 666 buys / 429 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x95ffb3a4b6764fb4549464c2677daed3c0e78b4e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/playzap-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
