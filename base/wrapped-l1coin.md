---
token: Wrapped L1coin
ticker: WL1
network: base
risk_score: 84
status: high
date: 2026-09-30
---

# Wrapped L1coin (WL1) — Smart Contract Security Analysis | Base

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-l1coin-base)

---

## Audit Summary

The HypERC20 contract functions as an upgradeable ERC-20 token with cross-chain capabilities. It features a robust ownership model managed by a multisig. Key administrative functions are restricted to the owner, but two significant issues were identified: privileged token minting by the 'mailbox' role and a state variable shadowing vulnerability. These findings introduce potential economic and technical risks that require attention.

> **Final Recommendation:** It is recommended to thoroughly review the logic within the `transferRemote` and `handle` functions to ensure that token minting is strictly controlled and aligns with the intended cross-chain bridge mechanics, potentially implementing additional safeguards or monitoring for these operations. The identified state variable shadowing issue should be immediately addressed by renaming the conflicting variable to prevent potential logic errors and ensure predictable contract behavior. Furthermore, ensure that the `mailbox` role, which has significant power over token supply, is managed with the highest security standards and transparency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The HypERC20 contract functions as an upgradeable ERC-20 token with cross-chain capabilities, leveraging the TokenRouter and MailboxClient for interchain communication. Key administrative functions… |
| **Governance / Economics** | 1/10 | High | The contract's ownership is securely managed by a 3/5 multisig, which is a strong governance practice for critical administrative actions like `transferOwnership` and `setInterchainSecurityModule`… |
| **Upgrades** | 1/10 | High | The contract is implemented as an upgradeable proxy, allowing for future enhancements and bug fixes, with the proxy admin also controlled by a 3/5 multisig, providing a robust upgrade path (7.7… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CD-01` — Shadowing state  *(Severity: High · Status: Unresolved)*



**Recommendation:** Review the flagged functions; the static analyser reported this as `shadowing-state`.


### `CP-01` — A privileged address can mint new tokens  *(Severity: Medium · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: transferRemote(uint32,bytes32,uint256), handle(uint32,bytes32,bytes). Restricted to: mailbox.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x0974…fce6 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 63.1% of supply. Of that, 29.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 10.7% in wallets, 23.4% in other contracts. 303 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as GenesisL1 (L1), market cap $11M, rank #1230. 303 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $346K (DexScreener, all pools). 24h trading volume $222K (CoinGecko, all markets, daily snapshot). 24h trading volume $153K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-5 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $346K of DEX liquidity across 2 pools. Launch: 82 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe652...4b22`](https://basescan.org/address/0xe6522a891702cd2e8cc2a5182638c9da1dd44b22) |
| **Network** | Base |
| **Price** | $0.2425 |
| **24h Volume** | $153.2K |
| **Liquidity** | $345.6K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 63.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 115 buys / 109 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xde9ba4084bf0733a9d69e42e71e5fd140179df71)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-l1coin-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-30*
