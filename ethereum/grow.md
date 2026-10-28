---
token: Grow
ticker: GROW
network: ethereum
risk_score: 58
status: medium
date: 2026-10-28
---

# Grow (GROW) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grow-eth)

---

## Audit Summary

The protocol implements a standard ERC-20 token with centralized minting capabilities. The architecture is straightforward, relying on a two-step ownership transfer process to prevent accidental loss of control. While the contract is secure in its implementation of standard token logic, the centralization of the minting function presents a significant economic risk to token holders.

> **Final Recommendation:** The contract is technically sound. To improve trust, consider implementing a multi-signature wallet for the owner and issuer roles to prevent single points of failure. Additionally, consider adding a timelock to the minting function to provide transparency to the community before large supply increases occur.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin-like patterns for ERC-20 compliance and ownership management. 7.1 Architecture is clean, using a two-step ownership transfer to mitigate human error. 7.2… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance rely entirely on the issuer role. The owner can update the issuer, and the issuer can mint tokens up to a defined maxSupply. This creates a centralized trust model… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable, providing certainty to users regarding the contract's behavior. 7.8 Operations are limited to standard token… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 3 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows the designated issuer to create new tokens at will, up to the maxSupply limit. This centralizes control over the total supply and can lead to the dilution of existing token holders' value if the issuer acts maliciously or is compromised.

**Recommendation:** Restrict the minting capability by implementing a multi-signature requirement or a governance-based voting mechanism. Alternatively, document the minting schedule clearly to provide transparency to the community.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x9bbe…cf6a — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 44% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $159K (DexScreener, all pools). 24h trading volume $8K (CoinGecko, all markets, daily snapshot). 24h trading volume $233K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0934 on 2026-06-26; the price is now 99.5123% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 65.4% of supply. What remains: 61.7% in wallets, 3.7% in other contracts. 4,454 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Grow (GROW). 4,454 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $159K of DEX liquidity across 8 pools. Launch: 980 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1223...bca6`](https://etherscan.io/address/0x1223334444a7466fbf985b14e1f4edaf3883bca6) |
| **Network** | Ethereum |
| **Price** | $0.003245 |
| **24h Volume** | $140.2K |
| **Liquidity** | $69.2K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 2y |
| **Top-10 Holders** | 65.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 134 buys / 219 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x9f78fbfd4ae6a0251556764875d1c2a08681b7daf8c1461cbb72063412533f16)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grow-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
