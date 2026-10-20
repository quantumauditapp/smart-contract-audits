---
token: Wrapped REACT
ticker: REACT
network: ethereum
risk_score: 64
status: medium
date: 2026-10-07
---

# Wrapped REACT (REACT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-react-eth)

---

## Audit Summary

This audit covers the WrappedReact ERC-20 token contract. The contract implements standard token functionalities and includes a minting mechanism. A key finding is the presence of a privileged `mint` function, which allows an authorized address to create new tokens, posing a potential economic risk through supply dilution.

> **Final Recommendation:** It is crucial to carefully manage the `owner` address and any `authorizedminter` addresses. Consider implementing robust multi-signature wallets for both the owner and any authorized minters to ensure that critical actions, especially those involving token supply changes, require consensus from multiple trusted parties. Regular security reviews of the operational procedures for these privileged roles are also recommended to mitigate the risk of unauthorized minting or key compromise.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The WrappedReact contract provides standard ERC-20 token functionality, including `transfer`, `transferFrom`, and `approve`. The code appears straightforward with no complex transfer logic or unusual… |
| **Governance / Economics** | 1/10 | High | The contract utilizes an `Ownable` pattern, allowing the owner to manage critical administrative functions such as `authorizeMinter` and `deAuthorizeMinter` (7.5 Governance). The primary economic… |
| **Upgrades** | 4/10 | Medium | The WrappedReact contract is not designed as an upgradeable proxy (7.7 Upgrades). This means that once deployed, its logic cannot be modified. Any future changes or bug fixes would require deploying… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 96.7% |
| **Top-3 Unlocked** | ⚠️ 99.5% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — A privileged address can mint new tokens  *(Severity: Medium · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: mint(address,uint256). Restricted to: authorizedminter, authorizedminters.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 5 address(es) other than the owner/deployer. One of them — a wallet, 0x6524…8e1f — holds 96.7% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 74% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 54.3% of supply. Of that, 1.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 51.5% in wallets, 1.8% in other contracts. 6,501 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Reactive Network (REACT), market cap $5M, rank #1691. 6,501 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $87K (DexScreener, all pools). 24h trading volume $212K (CoinGecko, all markets, daily snapshot). 24h trading volume $66K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.237 on 2025-03-05; the price is now 98.1524% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 2-of-4 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $87K of DEX liquidity across 2 pools. Launch: 508 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8171...2fc5`](https://etherscan.io/address/0x817162975186d4d53dbf5a7377dd45376e2d2fc5) |
| **Network** | Ethereum |
| **Price** | $0.004324 |
| **24h Volume** | $48.9K |
| **Liquidity** | $64.0K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 54.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 131 buys / 118 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xbe69eb8ee10b3b51f9cdb4aa0d4c7fe83971a650)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-react-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-07*
