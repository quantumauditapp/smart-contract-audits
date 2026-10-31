---
token: Funds Are Safu
ticker: SAFU
network: bsc
risk_score: 11
status: low
date: 2026-10-31
---

# Funds Are Safu (SAFU) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 11/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/funds-are-safu-bsc-49f7)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone implementing a standard ERC-20 token with custom migration logic. Ownership has been renounced, effectively locking the privileged migration functions and ensuring the contract logic remains immutable. The architecture is robust due to the renounced ownership and the fixed nature of the minimal clone pattern.

> **Final Recommendation:** The contract is secure due to the renunciation of ownership and the immutable nature of the minimal clone deployment. No further action is required as the privileged functions are now dormant and cannot be triggered by any address.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a standard EIP-1167 minimal clone pattern, ensuring consistent logic deployment. 7.1 Architecture is sound, utilizing standard OpenZeppelin upgradeable libraries. 7.2 Code… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance risks are mitigated by the renunciation of ownership. No central entity can manipulate the poolState or migration parameters. The token functions as a standard ERC-20… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are not applicable as the contract is an EIP-1167 minimal clone. The implementation is immutable, and the proxy pattern used here does not support logic upgrades. This eliminates the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x81df…c90a — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 25.7% of supply. What remains: 8.6% in wallets, 17.0% in other contracts. 3,815 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,815 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $100K (DexScreener, all pools). 24h trading volume $711K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 0.99% on sell. Market: $100K of DEX liquidity across 7 pools. Launch: 21 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 21 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 21 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdd80...7777`](https://bscscan.com/address/0xdd806e436dda5588bf54061c11590c77ddc87777) |
| **Network** | BNB Chain |
| **Price** | $0.0005037 |
| **24h Volume** | $672.2K |
| **Liquidity** | $95.3K |
| **Volume / Liquidity** | 7.1× |
| **Token Age** | 21d |
| **Top-10 Holders** | 25.7% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 3358 buys / 2427 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x13b86fcf85c9c8f5c36593822d216b8893c25450)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/funds-are-safu-bsc-49f7)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
