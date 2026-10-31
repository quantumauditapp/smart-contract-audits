---
token: Bitcoin Frogs
ticker: FROGS
network: bsc
risk_score: 57
status: medium
date: 2026-10-31
---

# Bitcoin Frogs (FROGS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bitcoin-frogs-bsc)

---

## Audit Summary

The BnagentToken is a standard ERC-20 implementation with additional administrative controls. The contract features a centralized minter role capable of adjusting supply and restricting token transfers. While the code follows standard patterns, the high degree of centralization poses significant risks to token holders.

> **Final Recommendation:** To improve security, consider transitioning the minter role to a multi-signature wallet or a decentralized governance contract to prevent single-point-of-failure risks. Additionally, implementing a time-lock for sensitive administrative actions would provide users with notice before significant changes to token economics or transfer rules occur.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin-like ERC-20 logic, ensuring 7.1 Architecture and 7.2 Code Security compliance. 7.3 Access Control is implemented via a minter role, which is robustly… |
| **Governance / Economics** | 3/10 | High | The protocol exhibits significant 7.4 Economic and 7.5 Governance risks due to the centralized minter role. The ability to mint tokens and block addresses allows the controller to unilaterally impact… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, mitigating 7.7 Upgrades risks. 7.8 Operations are static and defined at deployment. No proxy patterns are utilized, ensuring the logic remains immutable. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 3 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The minter role has the authority to create new tokens at will, which can dilute the holdings of existing investors. This function is restricted to the minter address.

**Recommendation:** Restrict minting to a multi-signature wallet or implement a hard-coded supply cap that cannot be exceeded by the minter.


### `CP-05` — Administrative Transfer Switch  *(Severity: Medium · Status: Unresolved)*

The minter can toggle a switch that enables or disables token transfers globally. This allows the controller to halt all trading activity at their discretion.

**Recommendation:** Remove the global transfer switch or implement a decentralized voting mechanism to trigger such a state change.


### `CP-06` — Address Blacklisting Capability  *(Severity: Medium · Status: Unresolved)*

The minter can add specific addresses to a blocked list, preventing those holders from transferring or selling their tokens. This creates a risk of arbitrary censorship.

**Recommendation:** Limit the use of blacklisting to specific regulatory compliance scenarios and ensure the criteria for blocking are transparently documented.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 67.6% of supply. Of that, 11.7% burned, 44.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 10.8% in wallets, 0.7% in other contracts. 1,515 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,515 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $21K (DexScreener, all pools). 24h trading volume $218K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (frog). Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 1% on buy, 2% on sell. Market: $21K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8854...29ad`](https://bscscan.com/address/0x885417732c10f5eca16c70e28700a19cb39029ad) |
| **Network** | BNB Chain |
| **Price** | $0.00000002 |
| **24h Volume** | $217.9K |
| **Liquidity** | $21.5K |
| **Volume / Liquidity** | 10.1× |
| **Token Age** | 12h |
| **Top-10 Holders** | 67.6% of supply |
| **Buy / Sell Tax** | 1.0% / 2.0% |
| **24h Transactions** | 2208 buys / 3619 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x955c52f9bf850792709fcb5b7c6c776e67eb2b13)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bitcoin-frogs-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
