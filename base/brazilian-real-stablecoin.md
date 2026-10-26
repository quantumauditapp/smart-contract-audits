---
token: Brazilian Real Stablecoin
ticker: BRS
network: base
risk_score: 66
status: high
date: 2026-10-26
---

# Brazilian Real Stablecoin (BRS) — Smart Contract Security Analysis | Base

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/brazilian-real-stablecoin-base)

---

## Audit Summary

The BRS protocol is a complex, upgradeable token implementation utilizing LayerZero OFT standards and extensive access control. The architecture is robust, leveraging established libraries for proxy management and cross-chain messaging. While the protocol includes centralized administrative controls, these are typical for regulated or permissioned token assets requiring compliance features.

> **Final Recommendation:** The protocol is well-engineered. We recommend that the multisig signers maintain a transparent policy regarding the use of the 'freeze' and 'mint' functions to ensure community trust. Additionally, ensure that the private keys for the multisig are managed using hardware security modules (HSMs) or institutional-grade custody solutions.

Regularly rotate administrative roles and conduct periodic audits of the 'whitelister' and 'minter' role assignments to ensure that access remains limited to authorized entities only.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The codebase demonstrates high technical maturity, utilizing standard OpenZeppelin and LayerZero libraries for core functionality. 7.1 Architecture is modular, employing UUPS proxy patterns for… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance controls are centralized, granting significant power to the owner and designated roles. The protocol relies on a multisig for administrative actions, which mitigates… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are handled via the UUPS pattern, which is the current industry standard for gas-efficient and secure proxy management. The implementation is correctly separated from the proxy, ensuring… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-06` — Centralized Control Over User Transfers  *(Severity: Medium · Status: Unresolved)*

The contract includes a 'freeze' mechanism that allows privileged roles to block specific addresses from interacting with the token. This effectively gives the operator the power to censor transactions or lock user funds at will.

**Recommendation:** Implement a time-lock for administrative actions or move the 'freeze' authority to a decentralized governance contract to prevent unilateral abuse of power.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xdcff…60c8 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 94% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 91.5% of supply. What remains: 24.8% in wallets, 66.7% in other contracts. 106 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Nora Brazilian Real Stablecoin (BRS), rank #6377. 106 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $33K (DexScreener, all pools). 24h trading volume $54K (CoinGecko, all markets, daily snapshot). 24h trading volume $150K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Stablecoin — backing unverified  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Its identity is not independently verified, so it gets none of the allowances an established stablecoin gets: every power its owner holds over supply and transfers is scored in full, because a peg is only as good as whoever can mint. Basis: CoinGecko category: Bridged Stablecoin. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-5 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $33K of DEX liquidity across 3 pools. Launch: 16 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.


### `QA-RECENT` — Recently launched — 16 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 16 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0000...b125`](https://basescan.org/address/0x0000006238e3c7797ae71827da303560bae1b125) |
| **Network** | Base |
| **Price** | $0.1834 |
| **24h Volume** | $130.6K |
| **Liquidity** | $31.6K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 16d |
| **Top-10 Holders** | 91.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 635 buys / 573 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x4a1d178e12878ff05fa8711ef13f671d25be1811)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/brazilian-real-stablecoin-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
