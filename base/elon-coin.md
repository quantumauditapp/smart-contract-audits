---
token: Elon Coin
ticker: ELON
network: base
risk_score: 70
status: high
date: 2026-10-24
---

# Elon Coin (ELON) — Smart Contract Security Analysis | Base

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/elon-coin-base)

---

## Audit Summary

The ClankerToken is a standard ERC-20 implementation with additional cross-chain capabilities via the Superchain Token Bridge. The architecture relies on the bridge contract to manage supply across chains. While the core token logic is robust, the privileged access granted to the bridge contract introduces significant centralization risks regarding token supply and individual user balances.

> **Final Recommendation:** The protocol should ensure that the Superchain Token Bridge remains secure, as it holds absolute authority over the token supply and user balances. We recommend implementing a multi-signature wallet or a timelock for the admin address to mitigate risks associated with the updateAdmin, updateImage, and updateMetadata functions.

Users should be aware that the token's supply is dynamic and controlled by the bridge. Continuous monitoring of the bridge contract's security posture is essential for maintaining the integrity of the token ecosystem.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes standard OpenZeppelin libraries for ERC-20, Votes, and Permit functionality, ensuring high code quality. 7.1 Architecture follows the cross-chain token standard (ERC-7802). 7.2… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risks are present due to the ability of the bridge to mint and burn tokens, which directly impacts supply and holder balances. 7.5 Governance is centralized under an admin role for… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not implemented via proxy patterns in this contract. 7.8 Operations are straightforward, with administrative functions limited to metadata and admin address management. The contract… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 7 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Privileged Minting Capability  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the Superchain Token Bridge to create new tokens at any time. This increases the total supply and dilutes the value held by existing token holders. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure the bridge contract is audited and restricted to authorized cross-chain operations only. Consider adding a supply cap if the tokenomics require protection against infinite minting.


### `CP-02` — Privileged Balance Manipulation  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the Superchain Token Bridge to remove tokens from any user's balance. This grants the bridge the power to effectively seize or destroy user assets. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement strict access controls and monitoring for the bridge contract. Ensure that burn operations are only triggered by legitimate cross-chain transfer requests initiated by the user.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 100.0% in wallets, 0.0% in other contracts. 4,813 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,813 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.3M (DexScreener, all pools). 24h trading volume $58.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (elon). Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.3M of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6665...3b07`](https://basescan.org/address/0x66650590ff805a33f7c81dd63e948dedc55c3b07) |
| **Network** | Base |
| **Price** | $0.000102 |
| **24h Volume** | $58.64M |
| **Liquidity** | $10.31M |
| **Volume / Liquidity** | 5.7× |
| **Token Age** | 7h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1708 buys / 1581 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xc11b18b570b6e9d30cb8e36f55c466ae707d8d57)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/elon-coin-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
