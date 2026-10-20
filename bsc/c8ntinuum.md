---
token: c8ntinuum
ticker: CTM
network: bsc
risk_score: 60
status: medium
date: 2026-09-29
---

# c8ntinuum (CTM) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/c8ntinuum-bsc)

---

## Audit Summary

The CTM token contract is an ERC-20 compliant token with access control features. The primary finding is the presence of a minting capability, allowing a privileged role to increase the token supply. This introduces a potential for token dilution if not managed carefully.

> **Final Recommendation:** It is crucial to establish and communicate a clear policy regarding the `MINTER_ROLE` and the conditions under which new tokens may be minted. Ensure that the address holding the `MINTER_ROLE` is secured with multi-signature wallets or robust governance mechanisms to prevent unauthorized supply inflation. If minting is not intended for the long term, consider renouncing the `MINTER_ROLE` or implementing a time-locked mechanism for its removal.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard ERC-20 token functionalities, including `transfer`, `balanceOf`, and `approve`. It utilizes OpenZeppelin's `AccessControl` for managing permissions, ensuring that… |
| **Governance / Economics** | 1/10 | High | The economic model of the CTM token allows for supply inflation through the `mint` function, which is controlled by an address holding the `MINTER_ROLE`. This capability introduces a risk of token… |
| **Upgrades** | 3/10 | High | The CTM contract is not designed as an upgradeable proxy, meaning its logic is immutable once deployed. This eliminates potential risks associated with upgrade mechanisms, such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 65.5% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 3 Informational_

### `CP-01` — Privileged Address Can Mint New Tokens  *(Severity: Medium · Status: Unresolved)*

A specific role, designated as the 'MINTER_ROLE', has the ability to create new CTM tokens using the `mint(address account, uint256 value)` function. This means that an address holding this role can increase the total supply of CTM tokens, which could dilute the value of tokens held by existing holders.

**Recommendation:** Token holders should understand that the total supply of CTM tokens can be increased by the address holding the 'MINTER_ROLE'. It is recommended to verify who holds this role and what policies or governance procedures are in place to control its use. If minting is not a desired long-term feature, consider removing the 'MINTER_ROLE' or transferring it to a burn address.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0xd5fa…25d9 — holds 65.5% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $5.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $39K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 17.6% of supply. What remains: 14.4% in wallets, 3.3% in other contracts. The deployer/owner wallet itself holds 6.9%. 11,826 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as c8ntinuum (CTM). 11,826 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner key. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 1 pools. Launch: 111 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc8fb...8888`](https://bscscan.com/address/0xc8fb80fcc03f699c70ff0cc08c09106288888888) |
| **Network** | BNB Chain |
| **Price** | $0.2301 |
| **24h Volume** | $39.1K |
| **Liquidity** | $8.9K |
| **Volume / Liquidity** | 4.4× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 17.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 529 buys / 498 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xa966c3877d2c372b36e141ad21d5cd74ff343f3b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/c8ntinuum-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-29*
