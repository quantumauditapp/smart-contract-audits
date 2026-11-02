---
token: BNC玩家
ticker: BNC玩家
network: bsc
risk_score: 24
status: low
date: 2026-11-02
---

# BNC玩家 (BNC玩家) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bnc-bsc-7495)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone implementation of an ERC-20 token with tax and migration mechanics. Ownership has been permanently renounced, rendering the privileged migration functions dormant and immutable. The contract architecture is standard for minimal clones, and no critical vulnerabilities were identified in the current state.

> **Final Recommendation:** The protocol is in a secure, immutable state due to the renunciation of ownership. No further action is required for the current implementation. Users should monitor the token for any unexpected behavior in transfer logic, though the code appears standard for a tax-enabled token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a robust EIP-1167 minimal clone pattern, ensuring consistent logic deployment. 7.1 Architecture and 7.2 Code Security are sound, adhering to standard OpenZeppelin library… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance risks are mitigated by the renunciation of ownership. No central party can trigger the migration functions or adjust tax parameters. The economic model is now fixed… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are not applicable as the contract is an EIP-1167 minimal clone. The implementation logic is permanently bound to the proxy bytecode. There is no risk of malicious logic updates or proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x14e5…be4a — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 31.5% of supply. What remains: 13.8% in wallets, 17.7% in other contracts. 2,097 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,097 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $26K (DexScreener, all pools). 24h trading volume $163K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 2.97% on sell. Market: $26K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xab16...7777`](https://bscscan.com/address/0xab165b81b551b8ad891e0b451a54075c9e067777) |
| **Network** | BNB Chain |
| **Price** | $0.00008114 |
| **24h Volume** | $162.9K |
| **Liquidity** | $26.2K |
| **Volume / Liquidity** | 6.2× |
| **Token Age** | 20h |
| **Top-10 Holders** | 31.5% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 2112 buys / 1866 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x769eb67bf5461c93a0474358212fdd8d6b0cccb2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bnc-bsc-7495)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
