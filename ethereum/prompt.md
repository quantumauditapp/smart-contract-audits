---
token: Prompt
ticker: PROMPT
network: ethereum
risk_score: 50
status: medium
date: 2026-10-25
---

# Prompt (PROMPT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/prompt-eth)

---

## Audit Summary

PromptToken is an ERC-20 compliant token integrated with LayerZero's OFT (Omnichain Fungible Token) standard. The contract utilizes AccessControl for granular permission management and includes custom logic for Wayfinder gateway integration. The primary risk identified involves the minting capabilities inherent to the cross-chain messaging architecture, which is standard for OFT implementations but requires careful monitoring of the endpoint configuration.

> **Final Recommendation:** Maintain the current multisig threshold for all privileged roles and ensure that the LayerZero endpoint address is monitored for any unauthorized configuration changes. Regularly audit the list of addresses granted the INVOKE_WAYFINDER_CONFIGURATION_ROLE to ensure adherence to the principle of least privilege.

Monitor cross-chain activity logs to detect any anomalous minting patterns that could indicate a compromise of the messaging endpoint. Ensure that the owner multisig remains active and that key management practices are strictly followed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows standard OpenZeppelin and LayerZero patterns, ensuring robust ERC-20 and OFT compliance. 7.1 Architecture is modular, separating cross-chain logic from core token state. 7.2… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance risks are centered on the ability of privileged roles to modify gateway configurations and cross-chain parameters. While the multisig owner provides a layer of… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not currently implemented as the contract is not a proxy. The immutability of the logic provides security against unauthorized code changes. Future upgrades would require a migration… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Privileged Minting via Cross-Chain Messaging  *(Severity: Medium · Status: Unresolved)*

The functions send, lzReceiveSimulate, and lzReceive allow for the minting of new tokens as part of the cross-chain transfer process. While this is intended for the OFT standard, it effectively allows the LayerZero endpoint to increase the total supply of the token, which could dilute existing holders if the endpoint or messaging protocol were compromised.

**Recommendation:** Ensure that the LayerZero endpoint is trusted and that the cross-chain messaging parameters are strictly configured. Implement monitoring to alert on large minting events that deviate from expected cross-chain volume.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x2751…5bdf — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 83.2% of supply. What remains: 9.7% in wallets, 73.5% in other contracts. The deployer/owner wallet itself holds 15.1%. 7,387 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Wayfinder (PROMPT), market cap $4M, rank #1835. 7,387 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $218K (DexScreener, all pools). 24h trading volume $4.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $273K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.607 on 2025-04-12; the price is now 97.2193% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-6 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $218K of DEX liquidity across 2 pools. Launch: 562 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x28d3...1544`](https://etherscan.io/address/0x28d38df637db75533bd3f71426f3410a82041544) |
| **Network** | Ethereum |
| **Price** | $0.01807 |
| **24h Volume** | $272.6K |
| **Liquidity** | $218.4K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 83.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 381 buys / 432 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xf7fd0860922bd3352e2dbaf725a182b74bf7a2e1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/prompt-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
