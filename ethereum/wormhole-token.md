---
token: Wormhole Token
ticker: W
network: ethereum
risk_score: 55
status: medium
date: 2026-10-12
---

# Wormhole Token (W) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wormhole-token-eth)

---

## Audit Summary

The WToken contract is an upgradeable ERC-20 token with burning, voting, and permit functionalities, built upon OpenZeppelin's secure and well-tested libraries. The contract utilizes a UUPS proxy pattern for upgradeability and implements robust access control for sensitive operations like minting, role management, and upgrades. No critical or high-severity vulnerabilities were identified during this audit. However, the centralized control over minting, role assignment, and contract upgrades introduces inherent governance and economic risks that require careful management by the controlling entity.

> **Final Recommendation:** To mitigate the inherent risks associated with centralized control, it is strongly recommended that all critical administrative roles (e.g., `MINTER_AND_BURNER_ADMIN`, upgrade role) be secured by a robust multi-signature wallet. This ensures that no single entity can unilaterally execute sensitive operations, thereby distributing trust and enhancing security. Additionally, transparent communication and community governance processes should be established for any proposed upgrades or significant changes to the token's economic parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The WToken contract is implemented as an ERC-20 token with additional features like burning, voting, and permits, leveraging battle-tested OpenZeppelin libraries (7.1 Architecture). The code… |
| **Governance / Economics** | 5/10 | Medium | The contract's economic model includes a minting capability, which is controlled by the `MINTER_ROLE`. The `grantMinterAndBurner` function, restricted to the `MINTER_AND_BURNER_ADMIN` role, allows… |
| **Upgrades** | 3/10 | High | The WToken contract utilizes the UUPS (Universal Upgradeable Proxy Standard) pattern, allowing for future upgrades to its logic contract (7.7 Upgrades). The `upgradeToAndCall` function facilitates… |

## Security Findings

_🟡 1 Medium · ⚪ 4 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — a contract — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `I-01` — No code-level findings — contract source is not verified on the explorer  *(Severity: Informational · Status: Acknowledged)*

The contract's source code has not been published or verified on the block explorer, so only its deployed bytecode and on-chain behaviour were available. No source-level vulnerability could be confirmed or ruled out. The assessment on this page rests on mint/owner authority, mint capability.

**Recommendation:** Treat an unverified contract as unaudited at the code level. Ask the team to verify the source on the explorer, which makes an independent review possible.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Wormhole (W), market cap $193M, rank #196. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $309K (DexScreener, all pools). 24h trading volume $207.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $884K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1.66 on 2024-04-03; the price is now 98.2412% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $309K of DEX liquidity across 4 pools. Launch: 810 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb0ff...2b91`](https://etherscan.io/address/0xb0ffa8000886e57f86dd5264b9582b2ad87b2b91) |
| **Network** | Ethereum |
| **Price** | $0.02961 |
| **24h Volume** | $598.0K |
| **Liquidity** | $167.6K |
| **Volume / Liquidity** | 3.6× |
| **Token Age** | 2y |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 906 buys / 832 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x57f3f9fa14196f3208e422899f39581cad2ab5a2f807e3125d3ec91577fa153a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wormhole-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*
