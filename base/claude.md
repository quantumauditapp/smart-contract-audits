---
token: Claude
ticker: CLAUDE
network: base
risk_score: 53
status: medium
date: 2026-10-28
---

# Claude (CLAUDE) — Smart Contract Security Analysis | Base

> **Risk Score: 53/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/claude-base)

---

## Audit Summary

The ClankerToken is a standard ERC-20 implementation with cross-chain capabilities via the Superchain Token Bridge. The architecture relies on the bridge contract for minting and burning, which introduces centralized control over the token supply. While the code follows standard OpenZeppelin patterns, the ability for the bridge to manipulate user balances represents a significant trust requirement.

> **Final Recommendation:** Users should be aware that the Superchain Token Bridge holds the authority to mint and burn tokens, which is a necessary feature for cross-chain functionality but requires trust in the bridge's security. We recommend implementing a multi-signature wallet for the admin role to mitigate risks associated with single-key compromise for metadata updates.

Ensure that the bridge contract address is correctly configured and monitored. Regular audits of the bridge infrastructure are essential, as the token's integrity is directly tied to the security of the cross-chain messaging protocol.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes robust OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, leveraging standard cross-chain interfaces. 7.2 Code Security is high… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic risks are centered on the centralized minting/burning authority. 7.5 Governance is currently limited to a single admin address for metadata updates. The protocol lacks decentralized… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not implemented in this contract, as it is a non-proxy deployment. The contract logic is immutable, which provides security against hidden logic changes. 7.8 Operations are… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xca9f…1a8b — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Centralized Minting Authority  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the Superchain Token Bridge to create new tokens at will. This increases the total supply and dilutes the value of existing holdings. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Document the minting policy clearly and ensure the bridge contract is secured by a multi-signature or decentralized governance mechanism.


### `CP-02` — Privileged Balance Manipulation  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the Superchain Token Bridge to remove tokens from any user's balance. This grants the bridge controller the power to effectively seize or destroy user assets. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement strict circuit breakers or timelocks on the bridge's ability to burn tokens to prevent unauthorized mass-burning of user funds.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 2.0% in wallets, 98.0% in other contracts. 4,834 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,834 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.2M (DexScreener, all pools). 24h trading volume $61.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.2M of DEX liquidity across 3 pools. Launch: 63 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0ed7...cb07`](https://basescan.org/address/0x0ed7e161d89865613f5fdc50d6bcb0410a06cb07) |
| **Network** | Base |
| **Price** | $0.000102 |
| **24h Volume** | $61.34M |
| **Liquidity** | $10.21M |
| **Volume / Liquidity** | 6.0× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1762 buys / 1615 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x91df32a199e3017fe7fbe18abf3a8969e6428d3c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/claude-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
