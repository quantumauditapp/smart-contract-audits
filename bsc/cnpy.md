---
token: CNPY
ticker: CNPY
network: bsc
risk_score: 59
status: medium
date: 2026-10-31
---

# CNPY (CNPY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 59/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cnpy-bsc)

---

## Audit Summary

The WCNPY contract is a standard ERC-20 token with administrative minting capabilities and a redemption mechanism. The protocol relies on a multisig owner for privileged operations, which mitigates single-point-of-failure risks. However, the ability for the owner to mint tokens and the specific implementation of the redemption process require careful monitoring by token holders.

> **Final Recommendation:** The protocol should maintain the current multisig configuration and ensure that all minting events are publicly communicated to the community to maintain transparency. 

Users should be aware that the owner possesses the authority to increase the total supply. We recommend implementing a timelock on the mint function to provide the community with advance notice of supply changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows standard OpenZeppelin patterns for ERC-20 and access control. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of established libraries. 7.3 Access… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risks are present due to the owner's ability to mint supply, which can impact token value. 7.5 Governance is centralized under a 3-of-3 multisig, providing a balance between security and… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. This ensures immutability of the logic, which is a strength for long-term trust. 7.8 Operations are straightforward, relying on standard… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CP-02` — Redemption Mechanism Risks  *(Severity: High · Status: Unresolved)*

The redeem function allows users to burn their own tokens to trigger a redemption request. While it only burns the caller's tokens, the reliance on an external address for off-chain processing introduces operational risk if the off-chain component fails to fulfill the request.

**Recommendation:** Ensure the off-chain redemption process is transparent and provide a clear SLA for fulfillment to protect users.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner can call the mint function to create new tokens at any time. This allows the controller to increase the total supply, which dilutes the value of existing holdings.

**Recommendation:** Implement a timelock on the mint function or transition to a decentralized governance model to approve supply increases.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x3421…22aa — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 92.1% of supply. What remains: 76.7% in wallets, 15.4% in other contracts. 14,765 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Canopy (CNPY), market cap $22M, rank #790. 14,765 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.2M (GeckoTerminal, all pools). 24h trading volume $2.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $565K (GeckoTerminal, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-3 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.2M of DEX liquidity across 20 pools. Launch: 55 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc69b...ddd2`](https://bscscan.com/address/0xc69b16cf18cea1e5d0bb6a1a9db802097790ddd2) |
| **Network** | BNB Chain |
| **Price** | $0.19065935 |
| **24h Volume** | $564.9K |
| **Liquidity** | $1.16M |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 92.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3414 buys / 4157 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xc69b16cf18cea1e5d0bb6a1a9db802097790ddd2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cnpy-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
