---
token: PUFFER
ticker: PUFFER
network: bsc
risk_score: 18
status: low
date: 2026-10-16
---

# PUFFER (PUFFER) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 18/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/puffer-bsc)

---

## Audit Summary

The PUFFER contract is an ERC-20 token implementing LayerZero's OFT standard, enabling cross-chain transfers. The audit identified one medium-severity issue: a privileged address (the LayerZero endpoint) can mint new tokens, which could lead to token dilution. The contract is owned by a multisig, which controls various operational parameters.

> **Final Recommendation:** It is strongly recommended to review and restrict the token minting capabilities of the LayerZero endpoint. If minting is essential for the protocol's design, implement strict controls such as a maximum mintable amount, a rate limit, or a governance-controlled minting process. Ensure the LayerZero endpoint address is highly secured, as compromise of this address would directly enable unauthorized token creation. Additionally, regularly review the multisig's operational procedures and ensure all administrative keys are securely managed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The PUFFER contract is an ERC-20 token that integrates LayerZero's Omnichain Fungible Token (OFT) functionality, allowing for seamless cross-chain transfers. The contract correctly implements… |
| **Governance / Economics** | 9/10 | Low | The contract utilizes an `Ownable` pattern, with ownership retained by a multisig wallet, enhancing security for critical administrative functions (7.3 Access Control). The owner can manage various… |
| **Upgrades** | 10/10 | Low | The PUFFER contract is not designed as an upgradeable proxy, meaning its logic cannot be altered post-deployment (7.7 Upgrades). This eliminates risks associated with upgradeability patterns, such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.5% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 5 Informational_

### `CP-01` — Privileged Address Can Mint New Tokens  *(Severity: Informational · Status: Unresolved)*

The contract allows a specific privileged address, identified as the LayerZero endpoint, to create new PUFFER tokens. This capability is exposed through the `send`, `lzReceiveSimulate`, and `lzReceive` functions. If this endpoint address were compromised or misused, an attacker could mint an arbitrary amount of new tokens, significantly increasing the total supply and diluting the value of existing token holders.

**Recommendation:** Token holders should be aware that the LayerZero endpoint has the power to mint new tokens. It is crucial for the protocol team to ensure this endpoint address is extremely secure and that its operations are transparent. Consider implementing safeguards such as a hard cap on the total supply, a maximum minting limit per transaction, or requiring a governance vote for any minting operations to protect against potential dilution.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The holder list from the security indexer adds up to 100.6% of supply, so it does not describe real balances. That happens with rebasing and reflection tokens, whose balances change without transfers, and with contracts that report balances they do not hold. Concentration is unknown and priced as an unknown — neither a whale nor safe.

**Recommendation:** Check the largest holders on the block explorer, which reads current balances.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Puffer (PUFFER), market cap $16M, rank #928. 13,012 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $623K (DexScreener, all pools). 24h trading volume $70.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $2.6M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.991 on 2024-12-07; the price is now 95.189% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Liquid Restaking Governance Tokens; a copy of the coin from its home chain (ethereum), minted here by LayerZero (lzReceive). Tokenomics — Supply: minted here by LayerZero (lzReceive) against tokens locked or burned on other chains. Control: a 3-of-6 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $623K of DEX liquidity across 8 pools. Launch: 523 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x87d0...92b6`](https://bscscan.com/address/0x87d00066cf131ff54b72b134a217d5401e5392b6) |
| **Network** | BNB Chain |
| **Price** | $0.04218 |
| **24h Volume** | $2.45M |
| **Liquidity** | $591.1K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 10992 buys / 11758 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xda7630a141dbb6382ddb6409aea7331da543b0bb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/puffer-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-16*
