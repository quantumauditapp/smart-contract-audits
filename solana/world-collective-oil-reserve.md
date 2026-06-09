---
token: World Collective Oil Reserve
ticker: WCOR
network: solana
risk_score: 90
status: critical
date: 2026-05-11
---

# World Collective Oil Reserve (WCOR) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/world-collective-oil-reserve-sol)

---

## Audit Summary

This audit report for the World Collective Oil Reserve (WCOR) SPL Token Mint identifies a critical data inconsistency: the token is reported as uninitialized, yet it exhibits active trading and liquidity. This fundamental contradiction raises severe concerns about the token's operational integrity and the reliability of the provided information. Additional risks include a lack of transparency regarding supply, decimals, and holder distribution, as well as the absence of external security signals. While mint and freeze authorities are appropriately revoked, the overall risk profile is elevated due to these significant uncertainties.

> **Final Recommendation:** The World Collective Oil Reserve (WCOR) token exhibits a critical data inconsistency regarding its initialization status, which fundamentally questions its validity as a tradable asset. This issue, combined with a lack of transparency on key tokenomics and external security validations, suggests a high-risk profile. While the revocation of mint and freeze authorities is a positive security measure, it does not mitigate the core concerns about the token's foundational state. Investors should exercise extreme caution and seek immediate clarification on the token's initialization status before engaging with this asset.

For projects seeking to establish a robust and transparent presence on Solana, a Premium Deploy option is recommended. This service includes comprehensive pre-deployment verification, enhanced on-chain data integrity checks, and integration with leading security analytics p…

## Security Analysis

This audit report for the World Collective Oil Reserve (WCOR) SPL Token Mint identifies a critical data inconsistency: the token is reported as uninitialized, yet it exhibits active trading and liquidity. This fundamental contradiction raises severe concerns about the token's operational integrity and the reliability of the provided information. Additional risks include a lack of transparency regarding supply, decimals, and holder distribution, as well as the absence of external security signals. While mint and freeze authorities are appropriately revoked, the overall risk profile is elevated due to these significant uncertainties.

The World Collective Oil Reserve (WCOR) token exhibits a critical data inconsistency regarding its initialization status, which fundamentally questions its validity as a tradable asset. This issue, combined with a lack of transparency on key tokenomics and external security validations, suggests a high-risk profile. While the revocation of mint and freeze authorities is a positive security measure, it does not mitigate the core concerns about the token's foundational state. Investors should exercise extreme caution and seek immediate clarification on the token's initialization status before engaging with this asset.

For projects seeking to establish a robust and transparent presence on Solana, a Premium Deploy option is recommended. This service includes comprehensive pre-deployment verification, enhanced on-chain data integrity checks, and integration with leading security analytics p…

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The technical analysis reveals a critical inconsistency: the token mint is reported as uninitialized, yet it exhibits active trading and liquidity on Dexscreener (7.2 Code Security). This fundamental  |
| **Governance / Economics** | 6/10 | Medium | Economically, the World Collective Oil Reserve token presents several risks. With a liquidity of $45,006 and a pair age of 50 days, the token is relatively new and has limited market depth, potentiall |
| **Upgrades** | 6/10 | Low | As an SPL Token, the core program logic is managed by the Solana Program Library and is not subject to project-specific upgrades (7.7 Upgrades). The revocation of mint and freeze authorities ensures t |

## Security Findings

_🔴 1 Critical · 🟡 2 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `C-01` — Critical Data Inconsistency Regarding Token Initialization  *(Severity: Critical · Status: Unresolved)*

The provided on-chain facts state the token mint is 'Initialized: False'. However, the token has reported liquidity ($45,006) and 24h trading volume ($11,845) from Dexscreener. An uninitialized SPL token mint cannot have supply, decimals, or be traded. This fundamental contradiction raises severe concerns about the token's operational status or the reliability of the provided data, making the token's integrity highly questionable.

**Recommendation:** Clarify the true initialization status of the token mint. If it is indeed uninitialized, all reported trading activity is highly suspicious and indicative of potential fraud. If the token is initialized, the data source for 'Initialized: False' should be corrected to reflect the actual on-chain state.


### `M-01` — Absence of External Security Signals  *(Severity: Medium · Status: Unresolved)*

There is no available data from external security signal providers such as GoPlus Solana or RugCheck. The absence of these independent validations means that common red flags, such as potential rug pulls, honeypots, or other malicious configurations, have not been assessed by specialized third-party tools, increasing the due diligence burden on users.

**Recommendation:** Engage with reputable security signal providers to obtain an independent assessment of the token's safety profile. This would provide an additional layer of trust and transparency for potential holders.


### `M-02` — Low Liquidity and Relatively New Pair Age  *(Severity: Medium · Status: Unresolved)*

The token has a relatively low liquidity of $45,006 and a pair age of only 50 days. Low liquidity can lead to significant price impact for trades, making it difficult for users to enter or exit positions without substantial slippage. A new pair age indicates limited time for market stability and community establishment, which can contribute to higher volatility and uncertainty.

**Recommendation:** Projects should aim to increase liquidity over time to support healthier trading and reduce price impact. A longer operational history and sustained liquidity build market confidence.


### `L-01` — Lack of Transparency on Token Supply and Decimals  *(Severity: Low · Status: Unresolved)*

The raw supply and decimal information for the token are reported as 'unknown'. While this is directly linked to the 'Initialized: False' status, even if initialized, the lack of readily available and verifiable data on these fundamental token parameters hinders a comprehensive understanding of the token's economics and potential for inflation or scarcity.

**Recommendation:** Ensure that all fundamental token parameters, including total supply and decimals, are accurately recorded and publicly accessible once the token mint is properly initialized. This is crucial for transparency and investor confidence.


### `L-02` — Lack of Holder Distribution Data  *(Severity: Low · Status: Unresolved)*

Information regarding holder concentration is unavailable. Without this data, it is impossible to assess the distribution of the token among holders, which is critical for understanding potential centralization risks. High concentration in a few wallets could indicate susceptibility to market manipulation or governance control by a small group.

**Recommendation:** Provide access to holder distribution data to allow for proper assessment of token centralization and potential risks associated with concentrated holdings.


### `I-01` — Revoked Mint and Freeze Authorities  *(Severity: Informational · Status: Resolved)*

Both the Mint Authority and Freeze Authority for the token have been revoked (set to None). This is a positive security measure, as it prevents any entity from minting new tokens (inflation) or freezing existing token accounts (restricting transfers) after deployment. This enhances the immutability and predictability of the token's supply and transferability.

**Recommendation:** Maintain the revoked status of these authorities to ensure the token's immutability and prevent unauthorized control over its supply and transfer functions.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`wcorvx...nazm`](https://solscan.io/account/wcorvxgcpiwe6evtdjxhjq6kcn4nwt9ubt1prjhnazm) |
| **Network** | Solana |
| **Price** | $0.01186 |
| **24h Volume** | $479.4K |
| **Liquidity** | $318.2K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 21d |
| **Top-10 Holders** | N/A of supply |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/8nsepc2tykgwbaz1wctuhi1cgnqmjupkcscteerjkj9b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/world-collective-oil-reserve-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-11*
