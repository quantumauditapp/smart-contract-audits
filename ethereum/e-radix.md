---
token: E-RADIX
ticker: EXRD
network: ethereum
risk_score: 54
status: medium
date: 2026-11-07
---

# E-RADIX (EXRD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/e-radix-eth)

---

## Audit Summary

The eXRD contract is a standard ERC-20 implementation with additional minting and ownership management capabilities. The architecture is straightforward, relying on established OpenZeppelin-style patterns for role-based access control. While the minting functionality introduces centralization risks, the code follows standard practices for token management.

> **Final Recommendation:** The protocol should ensure that the addresses assigned to the MinterRole are secured using multi-signature wallets to prevent unauthorized minting. Regular audits of the minter list are recommended to ensure only necessary entities retain the ability to issue new tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard ERC-20 logic for transfers and allowances, ensuring 7.1 Architecture and 7.2 Code Security standards are met. 7.3 Access Control is implemented via OwnerRole and… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the ability of privileged addresses to mint tokens. The mint(address,uint256) function allows minters to increase the total supply, which… |
| **Upgrades** | 2/10 | High | The contract is not upgradeable, which eliminates 7.7 Upgrades risks related to proxy patterns. The logic is immutable, providing certainty to users regarding the token's behavior. No proxy or beacon… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 63.2% |
| **Top-3 Unlocked** | ⚠️ 84.6% |

## Security Findings

_🟡 3 Medium · ⚪ 3 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows addresses with the MinterRole or OwnerRole to create new tokens at will. This centralizes control over the total supply and allows privileged users to dilute the holdings of existing token holders.

**Recommendation:** Restrict the minting capability to a multi-signature wallet or a time-locked governance contract to prevent unilateral supply changes. Consider implementing a hard cap on the total supply if the tokenomics allow for it.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 95.1% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a contract, 0x10bc…b029 — holds 63.2% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 93% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $58K (DexScreener, all pools). 24h trading volume $46K (CoinGecko, all markets, daily snapshot). 24h trading volume $39K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.66 on 2021-11-14; the price is now 99.9443% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 51.8% of supply. Of that, 8.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 40.4% in wallets, 2.7% in other contracts. 13,706 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as e-Radix (EXRD), rank #4406. 13,706 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $58K of DEX liquidity across 3 pools. Launch: 2186 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6468...9414`](https://etherscan.io/address/0x6468e79a80c0eab0f9a2b574c8d5bc374af59414) |
| **Network** | Ethereum |
| **Price** | $0.0003487 |
| **24h Volume** | $36.7K |
| **Liquidity** | $53.5K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 6y |
| **Top-10 Holders** | 51.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 139 buys / 109 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x684b00a5773679f88598a19976fbeb25a68e9a5f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/e-radix-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
