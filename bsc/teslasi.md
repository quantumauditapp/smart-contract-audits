---
token: TeslaSI
ticker: テスラSI
network: bsc
risk_score: 20
status: low
date: 2026-10-20
---

# TeslaSI (テスラSI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/teslasi-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with tax-enforced transfer logic. The contract ownership has been explicitly renounced on-chain, rendering all privileged administrative functions (such as migration controls) permanently inaccessible. The architecture is immutable, and the code follows standard OpenZeppelin patterns for upgradeable contracts, though the clone pattern itself prevents future logic upgrades.

> **Final Recommendation:** No security vulnerabilities were identified. Because ownership has been renounced, the contract is immutable and no further administrative actions can be taken. Users should be aware that the current tax and migration state is permanent and cannot be adjusted by any developer or owner.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a robust EIP-1167 minimal clone architecture, ensuring consistent logic across deployments. 7.1 Architecture is sound, utilizing standard ERC-20 and EIP-712 interfaces. 7.2 Code… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic parameters are fixed by the current state and cannot be altered by any party. 7.5 Governance is effectively non-existent as the owner has renounced control. 7.6 External dependencies are… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades are impossible for this contract due to the EIP-1167 clone pattern and the renounced ownership. 7.8 Operations are stable, as the contract logic is immutable and cannot be modified by… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 1 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5958...7777`](https://bscscan.com/address/0x5958c14c4013a2c87b32fcd629508eefb83f7777) |
| **Network** | BNB Chain |
| **Price** | $0.000154 |
| **24h Volume** | $285.9K |
| **Liquidity** | $40.1K |
| **Volume / Liquidity** | 7.1× |
| **Token Age** | 1d |
| **Top-10 Holders** | 35.5% of supply |
| **Buy / Sell Tax** | 3.0% / 2.6% |
| **24h Transactions** | 15694 buys / 2317 sells |

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

## Frequently Asked Questions

### Is TeslaSI a scam?

There is no definitive evidence to label TeslaSI as a scam. The contract is verified, ownership is renounced, and there is no mint function. However, the lack of locked liquidity and significant token concentration among the top 10 holders are common red flags in decentralized finance that investors should carefully evaluate before committing any capital to the asset.

### Is TeslaSI safe to buy?

Safety is subjective in decentralized finance. While the project features a verified contract with no minting capabilities, the lack of locked liquidity means funds are not technically protected from removal. Additionally, the 37.5% concentration in the top 10 wallets increases risk. Perform thorough due diligence, as these structural factors could impact your ability to exit positions at desired prices.

### Has TeslaSI been audited?

While the TeslaSI contract is verified on the BNB Chain explorer, this confirms the code matches its published source but does not equate to a professional security audit. Investors should understand that verification does not guarantee the absence of logic vulnerabilities or hidden risks within the smart contract architecture.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x242f28410c8979f05193ca2161702e064eb35a05)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/teslasi-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
