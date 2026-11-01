---
token: Super-Agent
ticker: SA
network: bsc
risk_score: 23
status: low
date: 2026-11-01
---

# Super-Agent (SA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/super-agent-bsc)

---

## Audit Summary

FlapTaxTokenV3 is an EIP-1167 minimal clone implementation of an ERC-20 token with migration-based state transitions. The contract ownership has been renounced on-chain, effectively disabling all administrative functions including migration controls. The architecture is immutable and secure against unauthorized state changes.

> **Final Recommendation:** The protocol is in a secure, immutable state due to the renunciation of ownership. No further action is required to secure the contract logic. Users should note that the migration state is permanently locked and cannot be altered by any party.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes standard OpenZeppelin upgradeable libraries adapted for minimal clones. 7.1 Architecture: EIP-1167 clone pattern ensures bytecode immutability. 7.2 Code Security: Standard… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic: The token logic relies on a fixed migration path that is now permanently locked. 7.5 Governance: No active governance exists as ownership is renounced. 7.8 Operations: The protocol… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades: The contract is an EIP-1167 minimal clone, which is inherently immutable. The implementation address is fixed at deployment and cannot be changed. There is no risk of malicious logic… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 26.0% of supply. What remains: 5.1% in wallets, 20.9% in other contracts. 1,338 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,338 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $41K (DexScreener, all pools). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $41K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x94f9...7777`](https://bscscan.com/address/0x94f952c2de8ef50aa2cefa5ce8df2f0fb5057777) |
| **Network** | BNB Chain |
| **Price** | $0.0001762 |
| **24h Volume** | $1.27M |
| **Liquidity** | $41.3K |
| **Volume / Liquidity** | 30.7× |
| **Token Age** | 4h |
| **Top-10 Holders** | 26.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11429 buys / 8953 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xc3f72d14ded2833c63e5b6c01ac81e7a87cedf4e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/super-agent-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
