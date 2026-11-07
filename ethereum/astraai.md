---
token: AstraAI
ticker: ASTRA
network: ethereum
risk_score: 70
status: high
date: 2026-11-07
---

# AstraAI (ASTRA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/astraai-eth)

---

## Audit Summary

The AstraAI token is a standard ERC-20 implementation with additional tax and liquidity management features. The contract exhibits high centralization, as the owner maintains significant control over transfer logic, fees, and blacklisting capabilities. While the code is functional and follows standard patterns, the presence of administrative backdoors necessitates caution for potential investors.

> **Final Recommendation:** Investors should be aware that the contract owner possesses the ability to modify transfer rules, blacklist addresses, and adjust fees at any time. We recommend that the project team considers transitioning ownership to a decentralized governance model or a time-locked multisig to mitigate these centralization risks.

For the development team, we suggest implementing a more transparent fee structure and removing the ability to blacklist individual holders to increase trust. Additionally, ensure that all mathematical operations are checked for potential rounding errors to maintain precision in tax calculations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows a standard ERC-20 structure with integrated tax logic. 7.1 Architecture and 7.2 Code Security are generally sound, utilizing OpenZeppelin standards. However, 7.3 Access… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance are heavily skewed toward the contract owner. The owner can unilaterally adjust buy/sell fees and blacklist addresses, directly impacting token liquidity and holder… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are managed via owner-restricted functions, which are transparent but carry significant centralization risks. No further… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 85.8% — Null Address, UNCX |
| **Top-1 Unlocked Holder** | 14.2% |
| **Lock Expiry** | Expired 147d ago |

## Security Findings

_🟠 1 High · 🟡 3 Medium · 🟢 2 Low · ⚪ 4 Informational_

### `QA-LIQUIDITY` — Liquidity lock has expired  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 85.8% still sits in UNCX, but that lock expired on 12 Jun 2026 — its owner can withdraw it at any moment. 14.2% is held, unlocked, by the token's owner/deployer (0x3049…8a24, 0xd603…08a9) — they can pull that liquidity at any moment. This is the rug-pull path.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-05` — Centralized Control over Transfer Swaps  *(Severity: Medium · Status: Unresolved)*

The manualSwap function allows the marketing wallet to trigger token swaps and withdraw ETH at will. This function acts as a switch that can influence the token's liquidity and price stability.

**Recommendation:** Implement a time-lock or a more automated, decentralized mechanism for triggering liquidity swaps to reduce reliance on a single wallet.


### `CP-06` — Administrative Blacklisting Capability  *(Severity: Medium · Status: Unresolved)*

The blacklist function allows the owner to prevent specific addresses from transferring or selling tokens. This creates a risk where holders can be arbitrarily restricted from accessing their assets.

**Recommendation:** Remove the blacklist functionality or restrict it to only address malicious actors via a transparent, community-voted process.


### `CP-07` — Arbitrary Fee Modification  *(Severity: Medium · Status: Unresolved)*

The owner can change buy and sell fees at any time using updateBuyFees and updateSellFees. This allows for potential 'honeypot' scenarios or sudden changes to the tokenomics.

**Recommendation:** Set a hard cap on the maximum fee percentage that can be set and consider using a time-lock for any fee adjustments.


### `CD-01` — Rounding Loss in Calculations  *(Severity: Low · Status: Unresolved)*

The swapAndLiquify function performs division before multiplication, which can lead to precision loss in token calculations.

**Recommendation:** Always perform multiplication before division to maintain maximum precision in financial calculations.


### `CP-08` — Dynamic Transaction Limits  *(Severity: Low · Status: Unresolved)*

The swapTokensAtAmount threshold can be modified by the owner, which affects how often the contract triggers liquidity swaps. This can be used to manipulate the frequency of automated market activity.

**Recommendation:** Define a fixed range for this threshold in the contract to prevent extreme adjustments.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 37.2% of supply. Of that, 2.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 6.4% in wallets, 28.8% in other contracts. 3,981 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as AstraAI (ASTRA), market cap $5M, rank #1677. 3,981 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $199K (DexScreener, all pools). 24h trading volume $131K (CoinGecko, all markets, daily snapshot). 24h trading volume $89K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $5.25 on 2024-03-13; the price is now 90.5411% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a 5-of-9 multisig. Code: not upgradeable (no proxy). Fees: 5% on buy, 5% on sell. Market: $199K of DEX liquidity across 1 pools. Launch: 1103 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0aa8...b95b`](https://etherscan.io/address/0x0aa8a7d1fb4c64b3b1dcea9a7ade81c59c25b95b) |
| **Network** | Ethereum |
| **Price** | $0.4959 |
| **24h Volume** | $89.5K |
| **Liquidity** | $199.3K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 3y |
| **Top-10 Holders** | 37.2% of supply |
| **Buy / Sell Tax** | 5.0% / 5.0% |
| **24h Transactions** | 65 buys / 36 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x4df1c47ecfbac8482a4811d373128e2acc007d02)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/astraai-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
