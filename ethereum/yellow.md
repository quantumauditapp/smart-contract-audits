---
token: Yellow
ticker: YELLOW
network: ethereum
risk_score: 20
status: low
date: 2026-10-21
---

# Yellow (YELLOW) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/yellow-eth)

---

## Audit Summary

YellowToken is a standard ERC-20 implementation utilizing OpenZeppelin's ERC20Permit and EIP712 standards. The contract follows established industry patterns for token functionality and does not contain any privileged administrative roles or custom transfer logic. No vulnerabilities were identified during the static analysis of the source code.

> **Final Recommendation:** The contract is well-structured and follows best practices for a standard ERC-20 token. No further action is required as the code is secure and lacks complex logic that could introduce vulnerabilities.

Users should ensure that they interact with the correct contract address and verify the token's total supply and distribution through block explorers to confirm the intended economic state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows the standard OpenZeppelin ERC-20 implementation, ensuring high compatibility with existing DeFi protocols. 7.1 Architecture is modular and 7.2 Code Security is robust due to… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance factors are not applicable as the token lacks minting, burning, or fee-based mechanisms. The token supply is fixed upon deployment, and there are no… |
| **Upgrades** | 8/10 | Low | The contract is not a proxy and is immutable, meaning 7.7 Upgrades are not possible. This eliminates risks associated with proxy logic, storage collisions, or malicious implementation updates. The… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x1ec1…ffb3 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 55% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.6% of supply. What remains: 1.5% in wallets, 98.1% in other contracts. 2,349 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Yellow (YELLOW), market cap $13M, rank #1061. 2,349 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $139K (DexScreener, all pools). 24h trading volume $826K (CoinGecko, all markets, daily snapshot). 24h trading volume $187K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $139K of DEX liquidity across 5 pools. Launch: 215 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x236e...2720`](https://etherscan.io/address/0x236eb848c95b231299b4aa9f56c73d6893462720) |
| **Network** | Ethereum |
| **Price** | $0.07755 |
| **24h Volume** | $93.0K |
| **Liquidity** | $76.1K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 99.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 243 buys / 161 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x59b2410d5055d223c132e722631b6c5939b56fdb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/yellow-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
