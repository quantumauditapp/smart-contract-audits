---
token: ElevateFi
ticker: EFI
network: polygon
risk_score: 75
status: high
date: 2026-10-28
---

# ElevateFi (EFI) — Smart Contract Security Analysis | Polygon

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/elevatefi-poly)

---

## Audit Summary

The EFI token is a standard ERC-20 implementation with integrated AccessControl for administrative functions. The contract includes centralized control mechanisms that allow privileged roles to mint tokens and burn tokens from arbitrary addresses. While the code follows standard OpenZeppelin patterns, the high level of centralization poses significant risks to token holders.

> **Final Recommendation:** It is recommended to implement a multi-signature wallet or a timelock controller for all privileged administrative functions to mitigate the risk of single-point-of-failure compromises. Additionally, the burn function should be restricted to user-initiated actions or strictly defined staking contract interactions to prevent unauthorized balance manipulation.

For future iterations, consider moving away from centralized minting and balance-burning capabilities to increase trustless decentralization. Ensure that any future changes to the tax logic account for precision loss by performing multiplication before division.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture utilizes standard OpenZeppelin AccessControl for role-based permissions. 7.1 Architecture and 7.2 Code Security are generally sound, utilizing well-tested libraries. However, 7.3… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are elevated due to the centralized nature of the token. The ability to mint new tokens allows for arbitrary supply inflation, directly impacting token value.… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are not implemented as this is a standard non-proxy contract. 7.8 Operations are managed via role-based access control, which is immutable regarding the contract structure itself. No… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `CP-02` — Unauthorized Balance Manipulation  *(Severity: High · Status: Unresolved)*

The burnFromStakingContract function allows a privileged role to burn tokens from any user's wallet, effectively allowing the controller to seize or destroy user funds.

**Recommendation:** Remove the ability to burn tokens from arbitrary addresses and restrict burning to the owner's own balance.


### `CP-01` — Centralized Minting Capability  *(Severity: Medium · Status: Unresolved)*

The mint function allows a privileged role to create new tokens at will, which can dilute the holdings of all existing token holders.

**Recommendation:** Restrict the minting capability to a decentralized governance process or cap the total supply to prevent arbitrary inflation.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x770b…edd6 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CD-01` — Rounding Loss in Tax Calculations  *(Severity: Low · Status: Unresolved)*

The _taxedTransfer function performs division before multiplication, which can lead to precision loss and minor discrepancies in tax collection.

**Recommendation:** Refactor the math logic to perform all multiplications before divisions to maintain precision.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 95.7% of supply. Of that, 2.2% burned, 6.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 84.5% in wallets, 2.9% in other contracts. 101,450 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as ElevateFi (EFI), market cap $2M, rank #2170. 101,450 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $386K (DexScreener, all pools). 24h trading volume $24K (CoinGecko, all markets, daily snapshot). 24h trading volume $37K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $117.96 on 2026-05-19; the price is now 97.2791% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 0% on buy, 5% on sell. Market: $386K of DEX liquidity across 2 pools. Launch: 433 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xae84...8169`](https://polygonscan.com/address/0xae840deab9916d80fadf42e218119a6051468169) |
| **Network** | Polygon |
| **Price** | $3.2200 |
| **24h Volume** | $37.3K |
| **Liquidity** | $386.2K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 95.7% of supply |
| **Buy / Sell Tax** | 0.0% / 5.0% |
| **24h Transactions** | 400 buys / 304 sells |

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

- [View on DexScreener](https://dexscreener.com/polygon/0xaec86dc2a08cd7cf8d90ee71d0e4864f25ba497b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/elevatefi-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
