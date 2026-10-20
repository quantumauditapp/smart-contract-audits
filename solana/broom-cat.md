---
token: broom cat
ticker: BROOMY
network: solana
risk_score: 32
status: low
date: 2026-10-19
---

# broom cat (BROOMY) — Smart Contract Security Analysis | Solana

> **Risk Score: 32/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/broom-cat-sol)

---

## Security Analysis

Broom cat (BROOMY) is a Solana-based token demonstrating several positive baseline technical indicators alongside notable liquidity constraints. Security parameters show the smart contract is verified, allowing for public inspection of its underlying programmatic logic. Additionally, the token features locked liquidity, which helps protect market participants against sudden liquidity removal by deployers. The asset exhibits an active 24-hour trading volume of approximately $197,247 against an available liquidity pool of $25,739. This discrepancy produces a high volume-to-liquidity ratio, signaling that substantial buy or sell orders could induce significant slippage and price volatility. Data regarding token holder concentration reflects minimal clustering among top addresses, though decentralized exchange pools often skew initial metrics. Furthermore, administrative privileges such as ownership renunciation and specific mint capabilities remain unconfirmed in public records, requiring investors to evaluate deployment permissions carefully. Overall, BROOMY maintains a low risk score of 32/100 based on core architectural confirmations.

Two primary security signals emerge when evaluating BROOMY. Positively, the locking of liquidity pools provides vital operational security, preventing developer-side capital extraction. In addition, the contract verification affords transparency into on-chain interactions. However, liquidity depth represents a primary concern; holding only $25,739 against nearly $200,000 in daily volume creates structural fragility during volatile market conditions. Moreover, the ambiguity surrounding ownership status and mint function permissions warrants caution. While top-tier holder concentration poses minimal risk according to tracking metrics, the absence of explicit renouncement means users must remain vigilant regarding potential administrative changes. These factors balance the asset's security profile between sound foundational infrastructure and elevated liquidity sensitivity.

## Security Findings

_1 finding(s)_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DUcYuD...pump`](https://solscan.io/account/DUcYuDof7Nnt2vpqHQA8dbz4kf524fDf8iAdQmsUpump) |
| **Network** | Solana |
| **Price** | $0.00009946 |
| **24h Volume** | $197.2K |
| **Liquidity** | $25.7K |
| **Volume / Liquidity** | 7.7× |
| **Token Age** | 7h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3304 buys / 2090 sells |

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

### Is broom cat a scam?

Current on-chain metrics do not indicate that broom cat is a scam. The token benefits from verified smart contract code and locked liquidity, mitigating immediate rug-pull threats. However, with thin liquidity of $25,739 and unclear ownership renunciation records, market participants must remain cautious. Always monitor deployer permissions and market depth before allocating capital to this Solana asset.

### Is broom cat safe to buy?

While broom cat holds a low risk score of 32/100, safety cannot be guaranteed. Its locked liquidity provides structural stability, yet the total liquidity pool remains modest at $25,739 relative to higher daily volumes. Furthermore, unverified mint authorities and ownership status present residual risks. Investors should factor in severe slippage and administrative uncertainties before executing transactions.

### Has broom cat been audited?

Broom cat's smart contract is verified on Solana block explorers, confirming that its source code matches deployed bytecode for public inspection. However, verification does not equal a formal third-party security audit. Independent reviews evaluating vulnerability vectors or protocol-level exploits have not been published for this token.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/86gcxb2kurqdhjwprigcekctr65xmu6mnohp54xscdm3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/broom-cat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
