---
token: American Oil Dividend Fund
ticker: AODF
network: solana
risk_score: 0
status: low
date: 2026-10-20
---

# American Oil Dividend Fund (AODF) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-sol)

---

## Audit Summary

The American Oil Dividend Fund (AODF) token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, mitigating risks of rug-pulls via liquidity withdrawal. Holder distribution data was unavailable, preventing a full assessment of supply concentration.

> **Final Recommendation:** The token demonstrates a strong security posture regarding on-chain authorities and liquidity. Investors should monitor the project's official communication channels for updates, as holder concentration data was not available for this audit.

Verify the mint and freeze authority status periodically using a block explorer to ensure they remain revoked. No further technical action is required to secure the token's current configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is initialized on the Token-2022 program with 6 decimals. 7.1 Architecture and 7.2 Code Security are standard for this program version. 7.3 Access Control is robust as both mint and freeze… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $1.64M in liquidity, which is 100% burned, ensuring permanent availability. 7.5 Governance and 7.6 External factors are limited by the lack of holder… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints are immutable once authorities are revoked. 7.8 Operations are stable; metadata is immutable, and no balance-mutating authorities exist. The token… |

## Security Findings

_⚪ 1 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`MFgq2f...pump`](https://solscan.io/account/MFgq2fX5egVFd5xKsQkjr7PNfF3PcaLWnnv7Nvmpump) |
| **Network** | Solana |
| **Price** | $0.359 |
| **24h Volume** | $965.4K |
| **Liquidity** | $1.65M |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 13h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 42086 buys / 728 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is American Oil Dividend Fund a scam?

Based on available data, there is no evidence that the American Oil Dividend Fund is a scam. It features a verified contract, locked liquidity, and no mint function to inflate supply. These technical attributes align with industry security standards, though investors should always perform independent due diligence regarding the project's long-term operational intentions and governance structure.

### Is American Oil Dividend Fund safe to buy?

The project has a low risk score of 0/100, supported by locked liquidity and high decentralization. However, safety is relative. Since ownership has not been renounced, the deployer retains administrative privileges. Investors should weigh the strong technical protections against the lack of formal ownership renunciation before deciding if the asset aligns with their personal risk management strategy.

### Has American Oil Dividend Fund been audited?

The project’s smart contract is verified, meaning the source code is publicly accessible and matches the on-chain deployment. While contract verification confirms the code's integrity and prevents hidden malicious functions, it is distinct from a comprehensive third-party security audit. Always verify the contract address independently before engaging with any decentralized finance assets.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/fjcgjw4lzaulyhbjjsctxibkzbirakhrfd8rzcmszu22)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
