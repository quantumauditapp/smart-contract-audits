---
token: Sophon
ticker: SOPH
network: ethereum
risk_score: 58
status: medium
date: 2026-10-23
---

# Sophon (SOPH) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sophon-eth)

---

## Audit Summary

The SophonToken is a standard ERC-20 implementation utilizing OpenZeppelin's battle-tested libraries. The architecture is straightforward, relying on standard token mechanics with no complex logic or blacklisting capabilities. The contract is managed by a 3-of-5 multisig, providing a robust governance structure for administrative tasks.

> **Final Recommendation:** The contract is well-structured and follows industry best practices for token implementation. No security vulnerabilities were identified during the analysis.

Maintain the current multisig security practices and ensure that the private keys for the 3-of-5 signers are stored in secure, geographically distributed hardware security modules (HSMs). Monitor the contract for any future interactions with malicious tokens if the rescue function is utilized.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin ERC-20 and EIP-712 permit implementations, ensuring high interoperability and security. 7.1 Architecture is clean and modular, adhering to established… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are managed by a 3-of-5 multisig wallet, which mitigates single-point-of-failure risks. The rescue function allows for the recovery of accidentally sent… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. The code is immutable, ensuring that the logic cannot be altered post-deployment. 7.8 Operations are supported by the rescue function… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0x3b18…9fcd) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.3% of supply. What remains: 44.6% in wallets, 45.7% in other contracts. 3,247 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Sophon (SOPH), market cap $8M, rank #1338. 3,247 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $80K (DexScreener, all pools). 24h trading volume $5.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $31K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.111 on 2025-05-28; the price is now 98.5423% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a 3-of-5 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $80K of DEX liquidity across 2 pools. Launch: 513 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6b77...d3f0`](https://etherscan.io/address/0x6b7774cb12ed7573a7586e7d0e62a2a563ddd3f0) |
| **Network** | Ethereum |
| **Price** | $0.001813 |
| **24h Volume** | $31.4K |
| **Liquidity** | $79.6K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 90.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 157 buys / 198 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xc511ff68ae3a1379e8ef3f599f88559c9ec77d9c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sophon-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
