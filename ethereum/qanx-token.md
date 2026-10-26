---
token: QANX Token
ticker: QANX
network: ethereum
risk_score: 65
status: high
date: 2026-10-26
---

# QANX Token (QANX) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/qanx-token-eth)

---

## Audit Summary

The QANX contract is a standard ERC-20 token implementation. The architecture is straightforward, relying on OpenZeppelin standards for core functionality. A minor issue regarding trapped ETH was identified, but the core token logic remains secure and standard.

> **Final Recommendation:** The contract is secure for standard ERC-20 operations. Users should be aware that the contract is not designed to handle native ETH, and any funds sent directly to the contract address will be permanently locked.

We recommend implementing a withdrawal function if the protocol intends to support native ETH, or adding a 'revert' statement in the receive/fallback functions to prevent accidental user loss.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes standard OpenZeppelin ERC-20 libraries, ensuring 7.1 Architecture and 7.2 Code Security compliance. 7.3 Access Control is implemented via a restricted chequeSigner role for… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance parameters are minimal as this is a standard utility token. The chequeSigner role is the only privileged actor, which is clearly defined. There are no complex… |
| **Upgrades** | 6/10 | Medium | The contract is not upgradeable, eliminating 7.7 Upgrades risks. 7.8 Operations are limited to standard token management. No proxy patterns are utilized. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 58.6% |
| **Top-3 Unlocked** | 76.5% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — change any holder's balance (seize or credit tokens); act through a hidden owner that survives an apparent renounce. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `CD-01` — Trapped ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract includes fallback and receive functions that allow it to accept native ETH, but it lacks any mechanism to withdraw or transfer these funds out of the contract. Any ETH sent to the contract address will be permanently locked.

**Recommendation:** If the contract is not intended to hold ETH, remove the receive and fallback functions. If it is intended to hold ETH, implement an administrative function to withdraw the balance.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 6 address(es) other than the owner/deployer. One of them — a wallet, 0x15dc…8d36 — holds 58.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 78.4% of supply. Of that, 37.0% burned, 0.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 37.0% in wallets, 4.0% in other contracts. 7,290 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as QANplatform (QANX), market cap $20M, rank #806. 7,290 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $320K (DexScreener, all pools). 24h trading volume $186K (CoinGecko, all markets, daily snapshot). 24h trading volume $46K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.203 on 2021-11-27; the price is now 94.0792% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $320K of DEX liquidity across 1 pools. Launch: 1341 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xaaa9...3aaa`](https://etherscan.io/address/0xaaa9214f675316182eaa21c85f0ca99160cc3aaa) |
| **Network** | Ethereum |
| **Price** | $0.01171 |
| **24h Volume** | $46.1K |
| **Liquidity** | $320.1K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 78.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 185 buys / 206 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x09117bff68b5939319e61b226bf1f3f5f985eba1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/qanx-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
