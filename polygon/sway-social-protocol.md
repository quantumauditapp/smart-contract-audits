---
token: Sway Social Protocol
ticker: SWAY
network: polygon
risk_score: 61
status: medium
date: 2026-10-24
---

# Sway Social Protocol (SWAY) — Smart Contract Security Analysis | Polygon

> **Risk Score: 61/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sway-social-protocol-poly)

---

## Audit Summary

CloutArtToken is a standard ERC-20 implementation with centralized administrative controls for minting and pausing. The architecture follows OpenZeppelin standards, ensuring robust base functionality. While the contract is secure in its logic, the centralization of power via AccessControl roles presents a trust-based risk for token holders.

> **Final Recommendation:** The protocol should consider transitioning the DEFAULT_ADMIN_ROLE and MINTER_ROLE to a multi-signature wallet or a decentralized governance contract to mitigate single-point-of-failure risks. Ensure that the private keys associated with these roles are stored in hardware security modules or institutional-grade custody solutions.

Regularly monitor the total supply and minting events to ensure transparency for the community. No further code changes are required for the current logic, as the identified risks are inherent to the chosen administrative model.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20 and AccessControl. 7.1 Architecture is standard, 7.2 Code Security is high due to 0.8.0 compiler usage, and 7.3 Access Control is… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centralized. The MINTER_ROLE allows for supply expansion, which directly impacts token value. 7.6 External dependencies are minimal, relying only on standard… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not supported as this is a non-proxy contract. 7.8 Operations are managed via standard role-based access control. The immutability of the contract logic provides a high degree of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 4 Medium · ⚪ 3 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows an address with the MINTER_ROLE to increase the total supply of tokens. This can lead to significant dilution of existing token holders' value if the role is compromised or misused.

**Recommendation:** Restrict the MINTER_ROLE to a multi-signature wallet or a time-locked governance contract to prevent unauthorized or sudden supply inflation.


### `CP-04` — Centralized Pause Control  *(Severity: Medium · Status: Unresolved)*

The pause and unpause functions allow an administrator to halt all token transfers globally. This creates a dependency on the administrator's availability and honesty, as they can effectively freeze user assets at will.

**Recommendation:** Implement a time-lock mechanism for the pause functionality to provide the community with notice before transfers are halted, or remove the pause functionality if it is not strictly required for business operations.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x3b1c…65d6 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 43% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $32K (DexScreener, all pools). 24h trading volume $11K (CoinGecko, all markets, daily snapshot). 24h trading volume $143K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.258 on 2021-10-20; the price is now 99.825% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.1% of supply. Of that, 4.0% burned, 6.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 29.1% in wallets, 50.5% in other contracts. 1,333 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Sway Social (SWAY), rank #8032. 1,333 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $32K of DEX liquidity across 5 pools. Launch: 1843 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x262b...b728`](https://polygonscan.com/address/0x262b8aa7542004f023b0eb02bc6b96350a02b728) |
| **Network** | Polygon |
| **Price** | $0.00114 |
| **24h Volume** | $129.5K |
| **Liquidity** | $13.8K |
| **Volume / Liquidity** | 9.4× |
| **Token Age** | 5y |
| **Top-10 Holders** | 90.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 880 buys / 784 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0x8cc823f7fa1d552d43ffe186a872185789a216f5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sway-social-protocol-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
