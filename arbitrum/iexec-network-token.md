---
token: iEx.ec Network Token
ticker: RLC
network: arbitrum
risk_score: 10
status: low
date: 2026-10-06
---

# iEx.ec Network Token (RLC) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/iexec-network-token-arb)

---

## Audit Summary

The RLCCrosschainToken is an upgradeable ERC-20 token designed for cross-chain functionality, managed by a multisig. The audit of the provided code map did not identify any critical or high-severity vulnerabilities. The contract utilizes standard and well-established patterns for upgradeability and access control, though the centralized control over token supply and roles by a multisig introduces inherent governance and economic considerations.

> **Final Recommendation:** Maintain stringent security practices for the multisig controlling the `DEFAULT_ADMIN_ROLE`, including secure key management and robust operational procedures. Regularly audit and monitor the addresses assigned to the `tokenbridge` role, as they have direct control over token supply. Implement a comprehensive testing and review process for all proposed upgrades to ensure no regressions or new vulnerabilities are introduced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The RLCCrosschainToken is an upgradeable ERC-20 token designed for cross-chain functionality, inheriting from `ERC20BridgeableUpgradeable` and `UUPSUpgradeable`. It implements standard ERC-20… |
| **Governance / Economics** | 9/10 | Low | The contract exhibits a centralized control model, where the `DEFAULT_ADMIN_ROLE` (managed by a 2/4 multisig) holds significant power, including the ability to grant/revoke roles and initiate… |
| **Upgrades** | 5/10 | Medium | The contract employs the UUPS proxy pattern, allowing for future upgrades of its logic. The `upgradeToAndCall` function, which facilitates these upgrades, is restricted to a specific role, ensuring… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 97.9% of supply. Of that, 87.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.4% in wallets, 6.1% in other contracts. 184 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as iExec RLC (RLC), market cap $63M, rank #423. Traded on Binance. 184 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $73K (DexScreener, all pools). 24h trading volume $168.5M (CoinGecko, all markets, daily snapshot). 24h trading volume $158K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $15.51 on 2021-05-10; the price is now 95.3396% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: bridge-mint functions in its code. Tokenomics — Supply: fixed — the contract has no mint function. Control: a 2-of-4 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $73K of DEX liquidity across 1 pools. Launch: 393 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe649...f47c`](https://arbiscan.io/address/0xe649e6a1f2afc63ca268c2363691cecaf75cf47c) |
| **Network** | Arbitrum |
| **Price** | $0.8928 |
| **24h Volume** | $157.9K |
| **Liquidity** | $72.8K |
| **Volume / Liquidity** | 2.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 97.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 447 buys / 514 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0x0eb43b37539a4261aa1860f9476094bb2c00a894)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/iexec-network-token-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
