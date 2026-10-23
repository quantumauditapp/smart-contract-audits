---
token: XAUt0
ticker: XAUT0
network: arbitrum
risk_score: 37
status: medium
date: 2026-10-23
---

# XAUt0 (XAUT0) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 37/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xaut0-arb)

---

## Audit Summary

The contract implements an upgradeable ERC-20 token with cross-chain functionality and centralized administrative controls. While the codebase leverages standard OpenZeppelin libraries, the protocol grants significant power to the owner and authorized senders, including the ability to mint, burn, and blacklist addresses. These features are inherent to the token's design but represent a high degree of centralization risk for end-users.

> **Final Recommendation:** The protocol should implement a time-lock mechanism for all administrative actions, particularly those involving minting, burning, or modifying the blocked list. This would provide transparency and a window for the community to respond to significant changes.

Additionally, consider formalizing the criteria for blacklisting addresses to reduce the risk of arbitrary asset seizure. Regular audits of the implementation contract are recommended whenever logic changes are proposed via the proxy.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes a standard Transparent Proxy pattern, ensuring upgradeability and separation of concerns. The code follows established patterns for ERC-20 and cross-chain messaging… |
| **Governance / Economics** | 8/10 | Low | The protocol is highly centralized, with the owner possessing unilateral control over supply and user access. The ability to destroy funds of blocked users and mint tokens at will creates significant… |
| **Upgrades** | 7/10 | Low | The contract uses a Transparent Proxy pattern, which is a battle-tested approach for upgradeability. Upgrades are controlled by a ProxyAdmin managed by a multisig, providing a robust security gate.… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 33.1% |
| **Top-3 Unlocked** | 76.4% |

## Security Findings

_🟠 1 High · ⚪ 7 Informational_

### `CD-01` — Shadowing State Variables  *(Severity: High · Status: Unresolved)*

The contract structure involves complex inheritance which may lead to state variable shadowing, where child contracts inadvertently overwrite or fail to access the intended state of parent contracts.

**Recommendation:** Perform a thorough review of the inheritance tree and use explicit naming or storage slots to ensure state variables are not shadowed.


### `CP-01` — Privileged Minting Capability  *(Severity: Informational · Status: Unresolved)*

The owner and authorized cross-chain senders can mint new tokens at any time, which dilutes the value of existing holdings.

**Recommendation:** Implement a hard cap on the total supply or require a multi-step governance process for minting events.


### `CP-02` — Administrative Control Over User Balances  *(Severity: Informational · Status: Unresolved)*

Privileged functions allow the owner or authorized senders to burn tokens from any address or move funds, effectively allowing them to seize user assets.

**Recommendation:** Restrict the ability to burn or move user funds to specific, transparent, and legally defined scenarios, or remove these functions entirely.


### `CP-06` — Address Blacklisting Capability  *(Severity: Informational · Status: Unresolved)*

The owner can add any address to a blocked list, preventing those users from transferring or selling their tokens.

**Recommendation:** Introduce a decentralized or community-voted mechanism for blacklisting to prevent unilateral abuse of this power.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 76.0% of supply. Of that, 5.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 17.5% in wallets, 53.3% in other contracts. 2,138 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Tether Gold Tokens (XAUT0), market cap $110M. 2,138 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $87K (DexScreener, all pools). 24h trading volume $3.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $52K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Gold. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: a 3-of-5 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $87K of DEX liquidity across 8 pools. Launch: 214 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4046...7159`](https://arbiscan.io/address/0x40461291347e1ecbb09499f3371d3f17f10d7159) |
| **Network** | Arbitrum |
| **Price** | $4,021.1800 |
| **24h Volume** | $34.9K |
| **Liquidity** | $35.2K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 76.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 127 buys / 110 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0xf87da73cfb22804ccd9562c714b6cbf06dc7d0cb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xaut0-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
