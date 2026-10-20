---
token: FOO
ticker: FOO
network: bsc
risk_score: 66
status: high
date: 2026-10-15
---

# FOO (FOO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/foo-bsc)

---

## Audit Summary

The FOOToken contract is an ERC-20 compatible token with several owner-controlled features. While it implements standard token functionalities, the audit identified significant centralization risks, including the owner's ability to control critical transfer parameters and blacklist users. A low-severity reentrancy vulnerability was also noted. The contract is not upgradeable.

> **Final Recommendation:** Address the reentrancy vulnerability in `_transfer` by implementing checks-effects-interactions pattern or using a reentrancy guard. Consider decentralizing critical administrative functions, such as blacklisting and setting the revenue wallet, by implementing a multi-signature wallet or a time-locked governance mechanism to reduce single points of failure and enhance trust. Review the necessity and scope of the owner's extensive control over transfer logic and emergency withdrawal functions, and explore options for community oversight or time-locks where appropriate.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The FOOToken contract implements core ERC-20 functionalities such as `balanceOf`, `transfer`, `transferFrom`, `approve`, and `allowance`. It includes emergency withdrawal functions… |
| **Governance / Economics** | 3/10 | High | The contract's governance model is straightforward, with a single owner controlling all privileged operations, which can simplify decision-making and execution. The owner can manage whitelists… |
| **Upgrades** | 6/10 | Medium | The FOOToken contract is not designed as an upgradeable proxy, which eliminates the complexities and potential risks associated with upgrade mechanisms, such as proxy implementation mismatches or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 37.0% — PinkLock02 |
| **Top-1 Unlocked Holder** | 0.3% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `CP-03` — Owner Can Redirect Token Flow and Fees  *(Severity: High · Status: Unresolved)*

The owner of the FOOToken contract has the ability to change the `revenueWallet` address using the `setRevenueWallet` function. This `revenueWallet` is critical because it can influence how token transfers are processed, potentially redirecting fees or affecting other token logic. This means a single owner can unilaterally alter a fundamental aspect of the token's operation.

**Recommendation:** Token holders should be aware that the owner can change the `revenueWallet` at any time, which could impact how their tokens are handled or if any fees are collected. For enhanced security and trust, consider implementing a multi-signature wallet or a time-lock for such critical changes, giving token holders more transparency and control.


### `CP-06` — Owner Can Block Token Holders  *(Severity: Medium · Status: Unresolved)*

The owner of the FOOToken contract can prevent specific addresses from transferring or selling their tokens by adding them to a `blacklist` using the `addToBlacklist` function. Conversely, they can remove addresses from this blacklist using `removeFromBlacklist`. This gives the owner the power to unilaterally freeze or unfreeze any token holder's assets.

**Recommendation:** Token holders should understand that the owner has the power to block their ability to move tokens. To reduce this centralized risk, consider implementing a decentralized governance mechanism or requiring a multi-signature approval for blacklisting actions, which would provide greater community oversight and protection against arbitrary actions.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

37.0% of the pool's LP is burned or time-locked. 37.0% is locked in PinkLock02 until 30 Jun 2028 (624 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. 2.6% is held, unlocked, by 9 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CD-01` — Potential Reentrancy Vulnerability in Token Transfers  *(Severity: Low · Status: Unresolved)*

The `_transfer` function, which is called by `transfer` and `transferFrom`, might be vulnerable to a reentrancy attack. This occurs when an external call is made before the contract's state (like balances) is fully updated. A malicious contract could re-enter the `_transfer` function multiple times before the initial call completes, potentially leading to incorrect balance deductions or other unintended behavior.

**Recommendation:** While the direct impact on token holders might be limited without further context on `_transfer`'s internal logic, this type of vulnerability can be exploited in complex scenarios. The project team should ensure that all state changes are completed *before* any external calls are made within the `_transfer` function to prevent reentrancy.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 21.9% of supply. Of that, 17.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.3% in wallets, 0.0% in other contracts. 8,788 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Football Genie (FOO), rank #4218. 8,788 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $100K (DexScreener, all pools). 24h trading volume $46K (CoinGecko, all markets, daily snapshot). 24h trading volume $46K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: 2.5% on buy, 2.5% on sell. Market: $100K of DEX liquidity across 1 pools. Launch: 285 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xac57...16ed`](https://bscscan.com/address/0xac57a9a2f40e7e5b59c87364771e653c8a2c16ed) |
| **Network** | BNB Chain |
| **Price** | $0.0002825 |
| **24h Volume** | $46.1K |
| **Liquidity** | $100.2K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 21.9% of supply |
| **Buy / Sell Tax** | 2.5% / 2.5% |
| **24h Transactions** | 211 buys / 206 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x0dcd8eb9f46229f84fb2a25f97942b6a6456ea21)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/foo-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
