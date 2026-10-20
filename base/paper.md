---
token: Paper
ticker: PAPER
network: base
risk_score: 68
status: high
date: 2026-10-13
---

# Paper (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/paper-base)

---

## Audit Summary

The ClankerToken contract is an ERC-20 token with additional features for burning, voting, and cross-chain operations. The audit identified significant centralized control, particularly concerning the `SuperchainTokenBridge` which can mint new tokens and burn tokens from any address. These capabilities pose a high risk to token holders through potential dilution and direct loss of funds.

> **Final Recommendation:** It is critical to establish robust governance and operational controls around the `SuperchainTokenBridge` address, as it holds significant power over the token supply and individual balances. Implement multi-signature wallets or time-locks for critical operations performed by this entity to mitigate risks of unauthorized minting or burning. Ensure transparency regarding the policies and procedures governing the `SuperchainTokenBridge`'s actions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements a standard ERC-20 token with extensions like ERC20Burnable, ERC20Votes, and ERC20Permit, demonstrating a robust foundation (7.1 Architecture). Access control is properly… |
| **Governance / Economics** | 3/10 | High | The economic model is significantly influenced by the `SuperchainTokenBridge`'s capabilities. This entity can `crosschainMint` new tokens, directly increasing the total supply and potentially… |
| **Upgrades** | 6/10 | Medium | The ClankerToken contract is not designed with an upgrade mechanism, such as a proxy pattern. This means the contract's logic is immutable once deployed, eliminating risks associated with… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 7 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xdd43…51d1 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Privileged Entity Can Create New Tokens  *(Severity: Informational · Status: Unresolved)*

The `crosschainMint` function allows a specific entity, the `SuperchainTokenBridge`, to create new Clanker tokens. This means that the total supply of tokens can be increased at any time by this entity, which could dilute the value of existing tokens held by others. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Token holders should understand that the `SuperchainTokenBridge` has the power to mint new tokens. It is crucial to ensure that the `SuperchainTokenBridge` is controlled by a secure and trusted entity, and its operational policies are transparent.


### `CP-02` — Privileged Entity Can Burn Tokens From Any Holder  *(Severity: Informational · Status: Unresolved)*

The `crosschainBurn` function grants the `SuperchainTokenBridge` the ability to remove Clanker tokens from any holder's balance. This means the `SuperchainTokenBridge` can reduce the token holdings of any address without their consent, which poses a significant risk to individual token ownership. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Token holders should be aware that the `SuperchainTokenBridge` possesses the capability to burn tokens from any account. Strong governance and operational controls over the `SuperchainTokenBridge` are essential to prevent unauthorized or malicious burning of tokens.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 100.0% in wallets, 0.0% in other contracts. 5,011 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,011 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.3M (DexScreener, all pools). 24h trading volume $51.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.3M of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x82b5...ab07`](https://basescan.org/address/0x82b5c90053c7ae91bc93dca945aeb3330b9eab07) |
| **Network** | Base |
| **Price** | $0.000102 |
| **24h Volume** | $51.41M |
| **Liquidity** | $10.31M |
| **Volume / Liquidity** | 5.0× |
| **Token Age** | 20h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2808 buys / 2664 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xfa4b7700a50cdb767d2dc7fd7d2dbcfcec16afc1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/paper-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-13*
