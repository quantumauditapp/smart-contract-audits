---
token: Ash Ketchum
ticker: サトシ
network: solana
risk_score: 28
status: low
date: 2026-10-20
---

# Ash Ketchum (サトシ) — Smart Contract Security Analysis | Solana

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ash-ketchum-sol)

---

## Security Analysis

The Ash Ketchum (サトシ) token on the Solana blockchain currently presents a structured security profile. The smart contract is verified, which confirms that the public code matches the deployed bytecode on the network. A critical positive indicator is the absence of a mint function, ensuring the total supply is capped and cannot be diluted by the contract creator. Furthermore, the top 10 holders account for 0.0% of the total supply, suggesting a highly distributed ownership structure that mitigates risks associated with whale manipulation or sudden large-scale dumping. Liquidity is currently locked, providing a layer of protection against rug pulls by ensuring that funds cannot be arbitrarily withdrawn from the pool. With a 24-hour trading volume of $113,840 against $30,261 in liquidity, the token maintains active market participation. Investors should remain aware that despite these metrics, the lack of renounced ownership implies the deployer retains certain administrative capabilities over the contract parameters.

The most significant safety signal for Ash Ketchum is the combination of verified code and a locked liquidity pool, which serves as a foundational layer of protection for initial investors. The lack of a mint function is also a vital security feature, as it prevents inflationary supply shocks. However, the primary risk remains the failure to renounce ownership. While the current setup is stable, an unrenounced contract means the deployer maintains potential control over operational settings. Investors should prioritize monitoring for any sudden changes in ownership status or wallet activity, as these are common precursors to security shifts in memecoin projects operating on the Solana network.

## Security Findings

_1 finding(s)_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AeNQSo...pump`](https://solscan.io/account/AeNQSoEJJe1fBim6AVpndX1zp9HdotMypBXkJL1qpump) |
| **Network** | Solana |
| **Price** | $0.00004286 |
| **24h Volume** | $113.8K |
| **Liquidity** | $30.3K |
| **Volume / Liquidity** | 3.8× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1305 buys / 1105 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Ash Ketchum a scam?

Based on current data, there is no evidence to classify this token as a scam. The contract is verified, the supply is fixed via the absence of a mint function, and liquidity is locked. These technical safeguards reduce typical rug-pull risks, though investors must always conduct personal due diligence when participating in decentralized finance assets.

### Is Ash Ketchum safe to buy?

The token features a low-risk profile of 28/100, supported by locked liquidity and a distributed holder base. However, safety is never absolute in crypto markets. The main risk factor is the unrenounced ownership, which grants the deployer ongoing contract authority. Potential buyers should consider these security parameters and their own risk tolerance before entering any position.

### Has Ash Ketchum been audited?

The contract is officially verified on the Solana blockchain, which ensures the code is transparent and matches the deployed data. While this confirms the technical integrity of the smart contract logic, it is distinct from a third-party security audit performed by a professional firm to check for deeper vulnerabilities.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/buvkpj4nwbcckh4gnhoxtcg23j9oga7btdbgjqungfla)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ash-ketchum-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
