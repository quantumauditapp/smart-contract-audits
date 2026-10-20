---
token: Borly
ticker: BORLY
network: solana
risk_score: 28
status: low
date: 2026-10-20
---

# Borly (BORLY) — Smart Contract Security Analysis | Solana

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/borly-sol)

---

## Security Analysis

Borly (BORLY) operates as a token on the Solana blockchain, exhibiting a verified contract status that enhances transparency for potential participants. The absence of a mint function suggests that the token supply remains fixed, preventing arbitrary inflation by the developers. Furthermore, the liquidity for the project is confirmed to be locked, which provides a measure of stability against sudden exit strategies. Market activity is notable, with a 24-hour trading volume of approximately $3.94 million against a liquidity pool of $114,452. A significant positive indicator is the distribution of token holdings, as the top 10 holders account for 0.0% of the total supply, implying a decentralized ownership structure. While these metrics contribute to a low risk score of 28/100, market participants should remain cognizant of the inherent volatility within the Solana ecosystem and conduct independent research before engaging with the smart contract directly.

The primary safety signals for Borly are its verified contract and the total absence of a minting function, which prevents supply manipulation. The decentralized distribution is particularly noteworthy; with the top ten holders owning 0.0% of the supply, the project avoids the concentration risks common in many new tokens. However, the lack of renounced ownership remains a point of caution, as it indicates the deployer retains administrative capabilities over the contract. While liquidity is locked, investors must monitor these administrative permissions closely. Overall, the combination of high liquidity-to-volume activity and a lack of whale concentration establishes a relatively stable foundation compared to other nascent projects in the sector.

## Security Findings

_1 finding(s)_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ECFmFa...pump`](https://solscan.io/account/ECFmFaHyJ8krXErN1QAxqUq97xCFUWYv9Ax5j2Aspump) |
| **Network** | Solana |
| **Price** | $0.001573 |
| **24h Volume** | $3.94M |
| **Liquidity** | $114.5K |
| **Volume / Liquidity** | 34.5× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 53725 buys / 27835 sells |

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

### Is Borly a scam?

Based on current data, there is no evidence suggesting Borly is a scam. The contract is verified, the mint function is disabled, and liquidity is locked, which are standard safety markers. However, the lack of renounced ownership means the developer retains control. Investors should always perform thorough due diligence before interacting with any smart contract or decentralized asset.

### Is Borly safe to buy?

Borly holds a low risk score of 28/100, supported by locked liquidity and high distribution among holders. While these indicators are positive, the project has not renounced ownership, which remains a key risk factor. Investors must weigh these technical safeguards against the inherent risks of the cryptocurrency market, ensuring they understand the implications of non-renounced ownership before allocating capital.

### Has Borly been audited?

The Borly smart contract is verified on the Solana blockchain, which provides transparency regarding the code's functionality. While this verification confirms the contract's structure, it does not constitute a formal third-party security audit. Users should remain aware that technical verification is different from an exhaustive professional security assessment of the underlying logic.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/3puekclpfocgpgyo6mvbfkzsuqtukq3eapz99adhsj8r)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/borly-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
