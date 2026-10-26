---
token: MUX Protocol
ticker: MCB
network: arbitrum
risk_score: 64
status: medium
date: 2026-10-26
---

# MUX Protocol (MCB) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mux-protocol-arb)

---

## Audit Summary

The ArbMCBv2 contract is an upgradeable ERC-20 token implementation on Arbitrum designed for cross-chain bridging. The architecture relies on centralized roles and gateway permissions to manage supply and cross-chain synchronization. While the core token logic is standard, the presence of privileged functions that can manipulate user balances and total supply introduces significant centralization risks.

> **Final Recommendation:** Token holders should be aware that the protocol administrators possess the technical capability to alter the total supply and individual user balances. It is recommended that the protocol transition to a decentralized governance model or implement time-locks on privileged functions to increase transparency and trust.

Ensure that the multisig signers are geographically and organizationally distributed to prevent collusion. Regular monitoring of the bridge gateway activity is advised to detect any unauthorized or anomalous minting/burning events.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract utilizes OpenZeppelin's upgradeable standards (7.1 Architecture) and follows standard ERC-20 patterns (7.2 Code Security). The implementation is clean and leverages established libraries… |
| **Governance / Economics** | 1/10 | High | Economic control is centralized within the bridge gateway and designated minter roles (7.4 Economic). Governance (7.5 Governance) is managed via a multisig proxy admin, providing a layer of… |
| **Upgrades** | 1/10 | High | The contract employs a Transparent Proxy pattern (7.7 Upgrades) managed by a multisig wallet. This setup allows for secure, controlled updates to the logic contract. The upgrade process is… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 4-of-8 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CP-02` — Privileged Balance Manipulation  *(Severity: High · Status: Unresolved)*

The bridgeBurn function allows the bridge gateway to directly reduce the balance of any user address. This grants the controller the power to remove tokens from any holder's wallet.

**Recommendation:** Restrict the ability to burn tokens to the user's own address or implement a circuit breaker that prevents mass-burning of user funds.


### `CP-01` — Privileged Minting Capability  *(Severity: Medium · Status: Unresolved)*

The functions bridgeMint and mint allow authorized addresses to create new tokens. This increases the total supply and dilutes the value of existing holdings.

**Recommendation:** Implement a hard cap on the total supply or require a multi-step governance process for any minting operations to prevent unauthorized supply expansion.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xc2d2…bebb — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 85.7% of supply. Of that, 3.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.5% in wallets, 72.9% in other contracts. 5,897 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as MUX Protocol (MCB), market cap $6M, rank #1472. 5,897 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $655K (DexScreener, all pools). 24h trading volume $38K (CoinGecko, all markets, daily snapshot). 24h trading volume $89K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $68.36 on 2021-10-16; the price is now 97.5033% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. The class itself adds no points; the contract and market facts decide the score. Basis: bridge-mint functions in its code. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $655K of DEX liquidity across 3 pools. Launch: 1507 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4e35...ce42`](https://arbiscan.io/address/0x4e352cf164e64adcbad318c3a1e222e9eba4ce42) |
| **Network** | Arbitrum |
| **Price** | $2.4000 |
| **24h Volume** | $87.5K |
| **Liquidity** | $635.7K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 4y |
| **Top-10 Holders** | 85.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 55 buys / 51 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0x4bbac3bbe0545f1ef3214af9b5dd842c7cab8846)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mux-protocol-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
