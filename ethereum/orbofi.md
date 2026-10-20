---
token: ORBOFI
ticker: OBI
network: ethereum
risk_score: 62
status: medium
date: 2026-10-15
---

# ORBOFI (OBI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/orbofi-eth)

---

## Audit Summary

The OBI contract is an ERC-20 token implementation utilizing OpenZeppelin's AccessControl. The audit found no critical, high, or medium severity vulnerabilities. The contract's core functionality appears robust, though it deviates from the full ERC-20 standard by omitting `totalSupply()`, `balanceOf(address)`, and `allowance(address,address)`.

> **Final Recommendation:** Ensure that the omission of standard ERC-20 functions (`totalSupply`, `balanceOf`, `allowance`) is intentional and compatible with all intended integrations. Conduct thorough testing of all administrative functions, particularly those related to role management, to confirm they operate as expected under various scenarios. Implement robust operational procedures (7.8 Operations) for managing the `DEFAULT_ADMIN_ROLE` to prevent unauthorized access or misuse.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The OBI contract implements a token with AccessControl (7.1 Architecture). It includes standard ERC-20 transfer functions (`transfer`, `transferFrom`, `approve`) but notably omits `totalSupply()`… |
| **Governance / Economics** | 1/10 | High | The contract's economic model (7.4 Economic) is straightforward, based on a standard token with no complex DeFi primitives. Governance (7.5 Governance) is managed through OpenZeppelin's… |
| **Upgrades** | 5/10 | Medium | The OBI contract is not deployed as a proxy (7.7 Upgrades) and therefore does not support upgradeability. This eliminates risks associated with proxy patterns, such as storage collisions or upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — change any holder's balance (seize or credit tokens). Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xe41b…6c4c — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 74.8% of supply. What remains: 3.5% in wallets, 71.3% in other contracts. 1,225 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Orbofi AI (OBI), market cap $2M, rank #2398. 1,225 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $36K (DexScreener, all pools). 24h trading volume $999K (CoinGecko, all markets, daily snapshot). 24h trading volume $107K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0848 on 2023-05-29; the price is now 98.5427% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $36K of DEX liquidity across 1 pools. Launch: 1171 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbb3a...1873`](https://etherscan.io/address/0xbb3a8fd6ec4bf0fdc6cd2739b1e41192d12b1873) |
| **Network** | Ethereum |
| **Price** | $0.001064 |
| **24h Volume** | $107.1K |
| **Liquidity** | $36.3K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 3y |
| **Top-10 Holders** | 74.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 259 buys / 236 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xe0498f8c24ea70724abd27cd9511daead3dbc0a0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/orbofi-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
