---
token: Onyxcoin
ticker: XCN
network: base
risk_score: 40
status: medium
date: 2026-10-25
---

# Onyxcoin (XCN) — Smart Contract Security Analysis | Base

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/onyxcoin-base)

---

## Audit Summary

The OptimismMintableERC20 contract is a standard bridge-compatible token implementation. It follows established patterns for cross-chain asset transfers. The architecture is robust, though it inherently relies on the security of the bridge controller to manage token supply.

> **Final Recommendation:** The contract is well-implemented for its intended purpose as a bridgeable asset. Ensure that the bridge contract address is managed by a secure multi-signature wallet or a robust governance mechanism to mitigate the risk of unauthorized minting.

Regularly monitor the bridge contract for any anomalous minting activity. No further code changes are required for the current implementation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin-style ERC20 logic, ensuring high compatibility and reliability. 7.1 Architecture follows the standard bridge-mintable pattern. 7.2 Code Security is… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risk is tied to the bridge's ability to mint tokens. 7.5 Governance is centralized within the bridge contract, which is expected for this architecture. The primary economic risk is the… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not applicable as this is a non-proxy contract. The implementation is immutable, which provides high security against logic changes. 7.8 Operations are standard for bridge-minted… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 92.5% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Privileged Minting Capability  *(Severity: Medium · Status: Unresolved)*

The mint function allows a privileged bridge address to create new tokens at will. This increases the total supply and dilutes the value of existing holdings.

**Recommendation:** Ensure the bridge address is secured by a multi-signature wallet and that minting events are monitored by an automated alerting system.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a wallet, 0xfcbc…139e — holds 92.5% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 67.8% of supply. Of that, 7.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.3% in wallets, 41.4% in other contracts. 74,822 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Onyxcoin (XCN), market cap $155M, rank #205. 74,822 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $178K (DexScreener, all pools). 24h trading volume $5.5M (CoinGecko, all markets, daily snapshot). 24h trading volume $60K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.184 on 2022-05-27; the price is now 97.8771% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: bridge — a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $178K of DEX liquidity across 5 pools. Launch: 833 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9c63...5e0c`](https://basescan.org/address/0x9c632e6aaa3ea73f91554f8a3cb2ed2f29605e0c) |
| **Network** | Base |
| **Price** | $0.004039 |
| **24h Volume** | $59.2K |
| **Liquidity** | $176.1K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 2y |
| **Top-10 Holders** | 67.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 378 buys / 576 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xcf307083dbf8b68be7f4bc24b0bc0d3bf79bfb54)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/onyxcoin-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
