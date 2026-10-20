---
token: MEBT
ticker: MEBT
network: polygon
risk_score: 77
status: high
date: 2026-10-20
---

# MEBT (MEBT) — Smart Contract Security Analysis | Polygon

> **Risk Score: 77/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mebt-poly)

---

## Audit Summary

The MEBT contract is a standard ERC-20 token with added tax and minting capabilities. It relies on centralized governance and oracle roles to manage supply and transfer fees. While the code is clean and follows standard OpenZeppelin patterns, the high degree of centralization poses significant risks to token holders.

> **Final Recommendation:** To improve security, consider implementing a multi-signature wallet or a time-lock mechanism for the governance role to prevent immediate, unilateral changes to token economics. Additionally, consider replacing the single oracle/rbs minting authority with a more decentralized mechanism or a hard-capped supply to protect holders from unexpected dilution.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes standard OpenZeppelin libraries for ERC-20, Burnable, and Permit functionality, ensuring 7.1 Architecture and 7.2 Code Security standards are met. 7.3 Access Control is… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance aspects are highly centralized. The governance role can arbitrarily modify transfer fees and whitelist addresses, directly impacting 7.6 External interactions. The… |
| **Upgrades** | 6/10 | Medium | The contract is not a proxy and does not support 7.7 Upgrades. The logic is immutable, which provides security against hidden logic changes but prevents patching if vulnerabilities are discovered. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 92.7% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 7.3% |

## Security Findings

_🟡 3 Medium · ⚪ 5 Informational_

### `CD-01` — Redundant Logic in Tax Rate Setters  *(Severity: Medium · Status: Unresolved)*

The functions setBuyRates and setSellRates contain redundant checks and logic structures that could be simplified to reduce the attack surface.

**Recommendation:** Refactor the tax rate setting logic into a single internal function to ensure consistency and reduce code duplication.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint function allows the oracle or rbs addresses to create new tokens at any time, which can dilute the value of existing holdings.

**Recommendation:** Implement a hard cap on the total supply or move the minting authority to a decentralized governance process.


### `CP-07` — Governance Control Over Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The governance role can change the tax rates for buys and sells at any time via setBuyRates and setSellRates, potentially impacting user liquidity.

**Recommendation:** Introduce a maximum fee cap or a time-lock delay for any changes to the tax rates.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.8% of supply. Of that, 6.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.3% in wallets, 93.1% in other contracts. 7,545 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

7,545 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

92.7% of the pool's LP is burned or time-locked. 44.0% is locked in PinkLock02 until 30 Jun 2029 (984 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. 16.1% is locked in PinkLock02 until 31 Jul 2029 (1015 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. 12.3% is locked in PinkLock02 until 31 Jul 2029 (1015 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. 10.6% is locked in PinkLock02 until 31 Aug 2029 (1045 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. 9.7% is locked in PinkLock02 until 31 Oct 2029 (1106 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. 7.3% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $475K (DexScreener, all pools). 24h trading volume $67K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 5% on sell. Market: $475K of DEX liquidity across 1 pools. Launch: 137 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x99d1...26d5`](https://polygonscan.com/address/0x99d11bb9bc5f1ee15a817934f33643dee41026d5) |
| **Network** | Polygon |
| **Price** | $2.4700 |
| **24h Volume** | $66.5K |
| **Liquidity** | $475.3K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 99.8% of supply |
| **Buy / Sell Tax** | 0.0% / 5.0% |
| **24h Transactions** | 1374 buys / 1479 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0x5b5158347c07e5b8e0343443a4c7cc1739a3d663)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mebt-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
