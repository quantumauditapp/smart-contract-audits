---
token: Edge
ticker: EDGE
network: ethereum
risk_score: 48
status: medium
date: 2026-10-21
---

# Edge (EDGE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/edge-eth)

---

## Audit Summary

EDGEToken is a standard ERC-20 token implementation. The contract ownership has been renounced, effectively disabling all privileged administrative functions, including minting and emergency fund recovery. The codebase is simple and adheres to standard ERC-20 patterns, resulting in a low-risk profile.

> **Final Recommendation:** No immediate actions are required as the contract is immutable and ownership is renounced. Users should be aware that the token supply is fixed and no further administrative changes can be made to the contract logic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows a standard ERC-20 implementation using OpenZeppelin libraries. 7.1 Architecture and 7.2 Code Security are robust due to the simplicity of the logic. 7.3 Access Control is… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance risks are minimal because the contract is immutable. Since ownership is renounced, no further supply inflation or governance changes can occur. The token supply is… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are straightforward with no ongoing maintenance requirements. The contract is permanently fixed in its current state. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 41.3% |
| **Top-3 Unlocked** | ⚠️ 93.2% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 4 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 79.4% of supply. Of that, 1.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 76.8% in wallets, 0.8% in other contracts. The deployer/owner wallet itself holds 72.6%. A holder that also controls the contract can sell into its own liquidity. 5,216 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 5 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Privileged Minting Functionality  *(Severity: Informational · Status: Unresolved)*

The contract contains a mint function that allows an owner to create new tokens. Because ownership has been renounced, this function is now permanently disabled and cannot be triggered by any address.

**Recommendation:** No action is required as the renouncement of ownership has effectively mitigated the risk of unauthorized minting.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Edge (EDGE), market cap $6M, rank #1534. 5,216 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $363K (DexScreener, all pools). 24h trading volume $88K (CoinGecko, all markets, daily snapshot). 24h trading volume $87K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1.52 on 2025-03-02; the price is now 90.1464% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $363K of DEX liquidity across 3 pools. Launch: 924 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4ec1...7831`](https://etherscan.io/address/0x4ec1b60b96193a64acae44778e51f7bff2007831) |
| **Network** | Ethereum |
| **Price** | $0.1518 |
| **24h Volume** | $87.0K |
| **Liquidity** | $363.0K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 2y |
| **Top-10 Holders** | 79.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 73 buys / 34 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x36095c32623186aa74257fc6729e2aa80ee17cee)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/edge-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
