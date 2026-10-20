---
token: PUFFER
ticker: PUFFER
network: bsc
risk_score: 34
status: low
date: 2026-10-16
---

# PUFFER (PUFFER) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 34/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/puffer-bsc)

---

## Audit Summary

The PUFFER contract is an ERC-20 token implementing LayerZero's OFT standard, enabling cross-chain transfers. The audit identified one medium-severity issue: a privileged address (the LayerZero endpoint) can mint new tokens, which could lead to token dilution. The contract is owned by a multisig, which controls various operational parameters.

> **Final Recommendation:** It is strongly recommended to review and restrict the token minting capabilities of the LayerZero endpoint. If minting is essential for the protocol's design, implement strict controls such as a maximum mintable amount, a rate limit, or a governance-controlled minting process. Ensure the LayerZero endpoint address is highly secured, as compromise of this address would directly enable unauthorized token creation. Additionally, regularly review the multisig's operational procedures and ensure all administrative keys are securely managed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The PUFFER contract is an ERC-20 token that integrates LayerZero's Omnichain Fungible Token (OFT) functionality, allowing for seamless cross-chain transfers. The contract correctly implements… |
| **Governance / Economics** | 1/10 | High | The contract utilizes an `Ownable` pattern, with ownership retained by a multisig wallet, enhancing security for critical administrative functions (7.3 Access Control). The owner can manage various… |
| **Upgrades** | 3/10 | High | The PUFFER contract is not designed as an upgradeable proxy, meaning its logic cannot be altered post-deployment (7.7 Upgrades). This eliminates risks associated with upgradeability patterns, such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.5% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Privileged Address Can Mint New Tokens  *(Severity: Medium · Status: Unresolved)*

The contract allows a specific privileged address, identified as the LayerZero endpoint, to create new PUFFER tokens. This capability is exposed through the `send`, `lzReceiveSimulate`, and `lzReceive` functions. If this endpoint address were compromised or misused, an attacker could mint an arbitrary amount of new tokens, significantly increasing the total supply and diluting the value of existing token holders.

**Recommendation:** Token holders should be aware that the LayerZero endpoint has the power to mint new tokens. It is crucial for the protocol team to ensure this endpoint address is extremely secure and that its operations are transparent. Consider implementing safeguards such as a hard cap on the total supply, a maximum minting limit per transaction, or requiring a governance vote for any minting operations to protect against potential dilution.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0xbb9c…6046 — holds 98.5% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 95% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The holder list from the security indexer adds up to 100.6% of supply, so it does not describe real balances. That happens with rebasing and reflection tokens, whose balances change without transfers, and with contracts that report balances they do not hold. Concentration is unknown and priced as an unknown — neither a whale nor safe.

**Recommendation:** Check the largest holders on the block explorer, which reads current balances.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Puffer (PUFFER), market cap $27M, rank #704. 13,012 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $623K (DexScreener, all pools). 24h trading volume $70.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $2.6M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.991 on 2024-12-07; the price is now 95.189% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Liquid Restaking Governance Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-6 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $623K of DEX liquidity across 8 pools. Launch: 523 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

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
