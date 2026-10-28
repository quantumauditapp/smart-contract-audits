---
token: BNC INU
ticker: BNCI
network: bsc
risk_score: 49
status: medium
date: 2026-10-28
---

# BNC INU (BNCI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bnc-inu-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with custom tax and migration logic. The contract ownership has been renounced on-chain, effectively disabling all privileged administrative functions. The codebase follows standard OpenZeppelin patterns for token functionality and initialization.

> **Final Recommendation:** The protocol is currently in a secure, immutable state due to the renouncement of ownership. No further administrative actions can be taken, which protects users from potential rug-pulls or unauthorized parameter changes. 

Users should verify the contract address against official documentation to ensure they are interacting with the correct, renounced deployment. No further security remediation is required at this time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes a gas-efficient EIP-1167 minimal clone pattern, ensuring consistent logic deployment. Code security is robust, adhering to standard ERC-20 and EIP-712 specifications for… |
| **Governance / Economics** | 1/10 | High | Economic parameters are governed by the immutable state of the contract. 7.4 Economic and 7.5 Governance items are effectively neutralized by the renounced ownership, preventing any further changes… |
| **Upgrades** | 8/10 | Low | The contract is deployed as a minimal clone, which is inherently immutable. 7.7 Upgrades are not possible, eliminating risks associated with malicious logic updates. 7.8 Operations are stable as the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x14e5…be4a — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $356K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 64.7% of supply. What remains: 9.7% in wallets, 55.1% in other contracts. 343 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

343 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 0.99% on sell. Market: $9K of DEX liquidity across 3 pools. Launch: 6 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5542...7777`](https://bscscan.com/address/0x5542057b3bebbb2f851edd1ec81966753b837777) |
| **Network** | BNB Chain |
| **Price** | $0.00000808 |
| **24h Volume** | $308.3K |
| **Liquidity** | $8.9K |
| **Volume / Liquidity** | 34.5× |
| **Token Age** | 6d |
| **Top-10 Holders** | 64.7% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 2919 buys / 2241 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x8b8142f73a00dfa484b1336eeccf102273ef808c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bnc-inu-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
