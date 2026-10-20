---
token: Pheasant Network Token
ticker: PNT
network: ethereum
risk_score: 83
status: high
date: 2026-10-06
---

# Pheasant Network Token (PNT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 83/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pheasant-network-token-eth)

---

## Audit Summary

The PheasantToken contract is an ERC-20 token with standard functionalities. It includes an owner-controlled minting function, which allows the owner to increase the total supply. This introduces a centralized risk where the owner can dilute existing token holders.

> **Final Recommendation:** The project should clearly communicate the centralized nature of the token's supply, specifically the owner's ability to mint new tokens. Consider implementing a multi-signature wallet for the owner address to enhance security and distribute control over critical functions like `mint`. For future iterations, explore mechanisms to decentralize control over token supply or introduce time-locks for sensitive operations to mitigate single points of failure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements the ERC-20 standard, providing essential token functionalities like transfer, approve, and balance queries (7.1 Architecture). The code appears to be a standard implementation… |
| **Governance / Economics** | 1/10 | High | The primary economic risk stems from the owner's ability to `mint` new tokens (7.4 Economic). This function, controlled by a single address, can increase the total supply at will, potentially… |
| **Upgrades** | 2/10 | High | The contract is not designed with an upgrade mechanism (7.7 Upgrades), meaning its logic is immutable once deployed. This eliminates risks associated with upgradeability, such as malicious upgrades… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `CP-01` — A privileged address can mint new tokens  *(Severity: Medium · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: mint(address,uint256). Restricted to: owner.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 100.0% in wallets, 0.0% in other contracts. 1 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $296K (DexScreener, all pools). 24h trading volume $939K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $296K of DEX liquidity across 5 pools. Launch: 6 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x02d5...0e93`](https://etherscan.io/address/0x02d54e48ea4dd76a408a7175d466bb8f578c0e93) |
| **Network** | Ethereum |
| **Price** | $0.06787 |
| **24h Volume** | $897.8K |
| **Liquidity** | $294.4K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 6d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 585 buys / 670 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x34d3516b0f0987b028770b68ba21c1e1939e3f13)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pheasant-network-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
