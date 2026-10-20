---
token: cheqd
ticker: CHEQ
network: ethereum
risk_score: 55
status: medium
date: 2026-10-04
---

# cheqd (CHEQ) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cheqd-eth)

---

## Audit Summary

The CosmosERC20 contract is a standard ERC-20 token implementation. Static analysis and review of key functions revealed no critical, high, or medium severity vulnerabilities. The contract lacks privileged functions, meaning no single entity can control transfers or modify core token behavior. This design contributes to a low overall risk profile.

> **Final Recommendation:** The CosmosERC20 contract is a straightforward ERC-20 implementation with no identified vulnerabilities. Its immutable nature and lack of privileged roles contribute to a robust security posture. Users should verify the contract address and ensure they are interacting with the intended token. For future deployments, consider implementing robust testing frameworks and formal verification for any custom logic, although this contract's simplicity makes such extensive measures less critical.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The CosmosERC20 contract implements a standard ERC-20 token (7.1 Architecture). All core ERC-20 functions are present and appear to adhere to the standard. The code map indicates no privileged… |
| **Governance / Economics** | 6/10 | Medium | The contract exhibits a decentralized economic model as it lacks any privileged functions that could influence token transfers or supply (7.4 Economic). There are no governance mechanisms or roles… |
| **Upgrades** | 6/10 | Medium | The CosmosERC20 contract is not implemented as a proxy and is therefore not upgradeable (7.7 Upgrades). This means its logic is immutable once deployed, eliminating upgrade-related risks such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 4 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x9960…25f8 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 92% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $50K (DexScreener, all pools). 24h trading volume $569K (CoinGecko, all markets, daily snapshot). 24h trading volume $57K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.716 on 2021-11-26; the price is now 99.6878% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The holder list from the security indexer adds up to 1.0388480599486825e+62% of supply, so it does not describe real balances. That happens with rebasing and reflection tokens, whose balances change without transfers, and with contracts that report balances they do not hold. Concentration is unknown and priced as an unknown — neither a whale nor safe.

**Recommendation:** Check the largest holders on the block explorer, which reads current balances.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as CHEQD Network (CHEQ), market cap $2M, rank #2239. 1,557 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $50K of DEX liquidity across 3 pools. Launch: 1643 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x70ed...4de7`](https://etherscan.io/address/0x70edf1c215d0ce69e7f16fd4e6276ba0d99d4de7) |
| **Network** | Ethereum |
| **Price** | $0.002335 |
| **24h Volume** | $55.4K |
| **Liquidity** | $45.5K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 4y |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 88 buys / 104 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xa305f3aad48e285c002a2dbadbbba58fea10ad45)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cheqd-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*
