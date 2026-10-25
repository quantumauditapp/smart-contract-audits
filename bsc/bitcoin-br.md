---
token: Bitcoin BR
ticker: BTCBR
network: bsc
risk_score: 19
status: low
date: 2026-10-25
---

# Bitcoin BR (BTCBR) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bitcoin-br-bsc)

---

## Audit Summary

The BEP20Token is a standard ERC-20 implementation on the BSC network. The contract ownership has been successfully renounced, effectively locking all administrative functions. The codebase is simple and follows standard patterns, with no active privileged controls remaining.

> **Final Recommendation:** The contract is secure due to its renounced ownership and standard implementation. No further action is required for the current deployment as it is immutable and functions as intended.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows a standard ERC-20 implementation with no complex logic. 7.1 Architecture and 7.2 Code Security are robust due to the simplicity of the transfer and approval mechanisms. 7.3… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are negligible because the contract is immutable. Since ownership is renounced, no entity can influence the token supply or economic parameters. The token… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not supported by this contract architecture. The contract is not a proxy, ensuring long-term immutability. 7.8 Operations are stable as no administrative actions are required for the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 96.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0x8ea1…20b0 — holds 96.3% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 78% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Privileged Minting Function is Dormant  *(Severity: Informational · Status: Unresolved)*

The mint(uint256) function allows for the creation of new tokens, which would dilute existing holders. However, because ownership has been renounced, this function is now permanently inaccessible.

**Recommendation:** No action required as the function is effectively disabled.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 25.5% of supply. Of that, 2.1% burned, 8.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 12.5% in wallets, 2.9% in other contracts. 149,367 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

149,367 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $76K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 30 pools. Launch: 1814 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0cf8...f262`](https://bscscan.com/address/0x0cf8e180350253271f4b917ccfb0accc4862f262) |
| **Network** | BNB Chain |
| **Price** | $0. |
| **24h Volume** | $51.8K |
| **Liquidity** | $13.2K |
| **Volume / Liquidity** | 3.9× |
| **Token Age** | 5y |
| **Top-10 Holders** | 25.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1155 buys / 1473 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x45c8d10a013c313d20984cfe4931fc276666b1df)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bitcoin-br-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
