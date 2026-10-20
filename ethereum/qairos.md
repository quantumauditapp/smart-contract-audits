---
token: Qairos
ticker: QRS
network: ethereum
risk_score: 25
status: low
date: 2026-10-12
---

# Qairos (QRS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 25/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/qairos-eth)

---

## Audit Summary

The LaunchToken contract is a standard ERC-20 token implementation. The audit found no critical, high, or medium severity vulnerabilities. The contract exhibits no privileged functions, ensuring decentralized control over token transfers and supply management.

> **Final Recommendation:** Ensure that the deployment process is secure and that the contract address is correctly communicated to users. Given the contract's simplicity and lack of privileged functions, the primary security considerations revolve around external interactions and user education. Users should be aware that the token's behavior is immutable and adheres strictly to the ERC-20 standard.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The LaunchToken contract implements the ERC-20 standard without any custom privileged functions, enhancing its security posture by minimizing potential attack vectors related to centralized control… |
| **Governance / Economics** | 6/10 | Medium | The contract is a pure ERC-20 token with no built-in governance mechanisms or complex economic models beyond standard token transfers (7.4 Economic). The complete absence of privileged functions… |
| **Upgrades** | 9/10 | Low | The LaunchToken contract is not implemented as a proxy and therefore does not support upgradeability (7.7 Upgrades). This eliminates risks associated with upgrade mechanisms, such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x3337…a32f — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 44.9% of supply. Of that, 2.9% burned — not holders that can sell, so excluded from the concentration score. What remains: 5.4% in wallets, 36.6% in other contracts. 326 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

326 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $46K (DexScreener, all pools). 24h trading volume $182K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $46K of DEX liquidity across 9 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe0bc...3fd1`](https://etherscan.io/address/0xe0bc2162104f64d0b399dede94aa72d0001a3fd1) |
| **Network** | Ethereum |
| **Price** | $0.0001425 |
| **24h Volume** | $160.8K |
| **Liquidity** | $44.5K |
| **Volume / Liquidity** | 3.6× |
| **Token Age** | 1d |
| **Top-10 Holders** | 44.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 553 buys / 414 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x687cdfb1db2cfa80a102e46a0ea9c290edaea2050131332eff224f72fe493c3d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/qairos-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*
