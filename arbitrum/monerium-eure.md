---
token: Monerium EURe
ticker: EURE
network: arbitrum
risk_score: 72
status: high
date: 2026-10-09
---

# Monerium EURe (EURE) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/monerium-eure-arb)

---

## Audit Summary

This report details a security audit of the Token contract, an upgradeable ERC-20 token on Arbitrum. The contract implements standard ERC-20 functionalities along with administrative roles for minting, account management, and a critical external validator for all transfers. A key finding highlights the significant centralization risk associated with the owner's ability to change the external validator contract, which directly controls all token transfer approvals.

> **Final Recommendation:** It is strongly recommended to review the role and control of the `validator` contract. Consider implementing a timelock or a more decentralized governance mechanism for changing the `validator` address to mitigate the single point of control risk. Additionally, ensure that all administrative roles and their associated permissions are clearly documented and regularly reviewed. For future upgrades, adhere to a rigorous testing and auditing process to prevent the introduction of new vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Token contract is an upgradeable ERC-20 implementation, inheriting from OpenZeppelin's robust libraries for access control and upgradeability (7.1 Architecture). It includes standard ERC-20… |
| **Governance / Economics** | 1/10 | High | The contract's ownership is managed by a 3-of-6 multisig, which enhances security for critical administrative functions such as adding/removing system/admin accounts, setting mint allowances, and… |
| **Upgrades** | 1/10 | High | The Token contract utilizes the UUPS proxy pattern, allowing for future upgrades to its logic (7.7 Upgrades). This provides flexibility for bug fixes or feature enhancements. The upgrade process is… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 4 Informational_

### `CP-03` — Centralized Control Over Token Transfer Validation  *(Severity: High · Status: Unresolved)*

The Token contract relies on an external `validator` contract to approve all token transfers. The owner of the Token contract, a multisig wallet, has the exclusive ability to change this `validator` contract at any time by calling the `setValidator` function. This means that whoever controls the owner multisig can effectively dictate whether any token transfer is allowed or blocked, or even redirect transfer logic to a malicious contract, without requiring any further community or token holder approval.

**Recommendation:** To reduce the centralization risk, consider implementing a timelock for changes to the `validator` address using the `setValidator` function. Alternatively, explore a more decentralized governance mechanism, such as a DAO vote, to approve changes to the `validator` contract. This would provide token holders with a say in critical transfer logic decisions and prevent a single entity from unilaterally controlling all token movements.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xfbc6…38c4 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 79.6% of supply. Of that, 1.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 66.7% in wallets, 11.8% in other contracts. 7,353 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Monerium EUR emoney (EURE), market cap $33M, rank #644. 7,353 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $114K (DexScreener, all pools). 24h trading volume $1.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $34K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Stablecoin — issuer-backed (fiat reserves)  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Its identity is not independently verified, so it gets none of the allowances an established stablecoin gets: every power its owner holds over supply and transfers is scored in full, because a peg is only as good as whoever can mint. Basis: CoinGecko category: EUR Stablecoin. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-6 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $114K of DEX liquidity across 2 pools. Launch: 513 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0c06...44f8`](https://arbiscan.io/address/0x0c06ccf38114ddfc35e07427b9424adcca9f44f8) |
| **Network** | Arbitrum |
| **Price** | $1.1200 |
| **24h Volume** | $34.2K |
| **Liquidity** | $114.4K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 79.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 52 buys / 65 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x529ed071c8c242659b19fa79308db84cef0393f0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/monerium-eure-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*
