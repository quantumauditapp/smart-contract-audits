---
token: Anthropic
ticker: ANTHROPIC
network: base
risk_score: 54
status: medium
date: 2026-11-05
---

# Anthropic (ANTHROPIC) — Smart Contract Security Analysis | Base

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anthropic-base-81ee)

---

## Audit Summary

The ClankerToken is a standard ERC-20 implementation with cross-chain capabilities via the Superchain Token Bridge. The architecture relies on the bridge contract to manage supply fluctuations. While the core token logic is standard, the privileged access granted to the bridge contract introduces significant centralization risks regarding token supply and individual user balances.

> **Final Recommendation:** The protocol should ensure that the Superchain Token Bridge remains secure, as it holds absolute authority over the token supply. Users should monitor bridge governance and security updates, as any compromise of the bridge contract directly impacts the integrity of the token balances.

For future iterations, consider implementing a timelock or multi-signature requirement for administrative actions to further decentralize control over metadata and bridge interactions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin standards for ERC-20, Votes, and Permit functionality. 7.1 Architecture follows standard cross-chain patterns, and 7.2 Code Security is robust due to… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the bridge's authority. The ability to mint and burn tokens at will allows for potential supply manipulation. While necessary for cross-chain… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not implemented as this is a non-proxy contract. 7.8 Operations are straightforward, with administrative functions limited to metadata updates. No complex upgrade paths exist to… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Privileged Minting Capability  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the bridge contract to increase the total token supply at any time. This can lead to the dilution of existing token holders' value if the minting process is not strictly governed by cross-chain bridge events. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure that the bridge contract logic is audited and that minting events are strictly tied to verified cross-chain messages to prevent unauthorized supply inflation.


### `CP-02` — Privileged Balance Modification  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function grants the bridge contract the authority to remove tokens from any user's balance. This allows the controller to effectively seize or destroy user assets without the holder's consent. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement strict circuit breakers or monitoring on the bridge contract to detect and alert on large-scale burn operations that could indicate a compromise.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 5,226 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,226 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.3M (DexScreener, all pools). 24h trading volume $53.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.3M of DEX liquidity across 1 pools. Launch: 365 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x191d...1796`](https://basescan.org/address/0x191d779ca90f2b626633b822581f2f7da61e1796) |
| **Network** | Base |
| **Price** | $0.000102 |
| **24h Volume** | $53.86M |
| **Liquidity** | $10.33M |
| **Volume / Liquidity** | 5.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2099 buys / 1968 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xdb680e077064a4da7d6e1c6197ac651c7254c06f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anthropic-base-81ee)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
