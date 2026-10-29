---
token: AEON
ticker: AEON
network: bsc
risk_score: 58
status: medium
date: 2026-10-29
---

# AEON (AEON) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aeon-bsc)

---

## Audit Summary

The AEON token is a standard ERC-20 implementation with additional administrative controls for minting and pausing. The contract architecture is straightforward and follows established OpenZeppelin patterns. However, the centralization of power in the Minter and Pauser roles introduces significant trust requirements for token holders.

> **Final Recommendation:** The protocol should consider transitioning the Minter and Pauser roles to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single point of failure. Additionally, implementing a time-lock on sensitive administrative actions would provide transparency and protection for token holders.

Users should be aware that the supply is not fixed and that the ability to pause transfers can be used to restrict liquidity at any time. We recommend monitoring the addresses assigned to these roles for any suspicious activity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard, battle-tested OpenZeppelin libraries for ERC-20 functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of audited base contracts. 7.3… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risks are present due to the minting capability, which allows for arbitrary supply inflation. 7.5 Governance is currently centralized, meaning token holders have no say in minting or… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not supported as this is a non-proxy contract. The logic is immutable once deployed. This eliminates risks associated with malicious implementation updates but prevents patching… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 4 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows the Minter role to create new tokens at will. This can lead to significant dilution of existing token holders' value if the role is compromised or misused.

**Recommendation:** Restrict the minting authority to a multi-signature wallet or a governance contract, and consider implementing a hard cap on the total supply.


### `CP-04` — Centralized Pause Control  *(Severity: Medium · Status: Unresolved)*

The pause and unpause functions allow the Pauser role to halt all token transfers globally. This creates a risk where users may be unable to move their funds during critical market conditions.

**Recommendation:** Limit the use of the pause functionality to emergency scenarios only, and ensure the Pauser role is held by a secure, multi-signature entity.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xc324…5cab — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 86.4% of supply. What remains: 8.3% in wallets, 78.2% in other contracts. 52,186 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as AEON (AEON), market cap $7M, rank #1503. 52,186 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $788K (GeckoTerminal, all pools). 24h trading volume $3.5M (CoinGecko, all markets, daily snapshot). 24h trading volume $555K (GeckoTerminal, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $788K of DEX liquidity across 20 pools. Launch: 95 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x277a...9b80`](https://bscscan.com/address/0x277add739c6e0477616948357af9e79fe1ec9b80) |
| **Network** | BNB Chain |
| **Price** | $0.02671377 |
| **24h Volume** | $555.1K |
| **Liquidity** | $782.1K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 86.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3519 buys / 4211 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x277add739c6e0477616948357af9e79fe1ec9b80)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aeon-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
