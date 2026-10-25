---
token: Wojak
ticker: WOJAK
network: ethereum
risk_score: 48
status: medium
date: 2026-10-25
---

# Wojak (WOJAK) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wojak-eth-8118)

---

## Audit Summary

The PangeaOFT contract implements an Omnichain Fungible Token (OFT) standard. The architecture relies on LayerZero for cross-chain messaging and includes specific roles for metadata management and supply reporting. While the code follows standard patterns, the ability for privileged roles to influence supply metrics introduces centralized trust requirements.

> **Final Recommendation:** The protocol should ensure that the addresses assigned to the 'supplyReporter' and 'metadataAuthority' roles are secured via multi-signature wallets or timelock contracts to mitigate the risk of single-point-of-failure compromise. Regular monitoring of supply-related events is recommended to detect any unexpected changes in the reported supply.

Given the centralized nature of these roles, transparency regarding the identity and security practices of the entities holding these keys is essential for maintaining user trust. No further code changes are required for the current implementation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes the robust LayerZero OFT standard, ensuring standard ERC-20 compatibility and cross-chain interoperability. 7.1 Architecture is well-structured, leveraging OApp modules for… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance aspects are centralized. The supplyReporter role has the authority to influence supply reporting, which impacts tokenomics. While restricted, this creates a dependency… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported via proxy patterns; the contract is immutable. 7.8 Operations are handled through administrative functions that allow for metadata updates and role management. The lack… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The 'supplyReporter' role can influence the reported supply of the token through the 'reportSupply' function. Additionally, the LayerZero endpoint can trigger minting via 'lzReceive' and 'lzReceiveSimulate'. This allows privileged entities to potentially alter the token's circulating supply metrics.

**Recommendation:** Implement a multi-signature wallet for the 'supplyReporter' role and consider adding a timelock to any functions that significantly alter supply parameters to provide transparency and prevent immediate, unauthorized actions.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xa6f3…e168 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 27.0% of supply. What remains: 7.1% in wallets, 19.9% in other contracts. 63 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

63 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $39K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (wojak). Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 1 pools. Launch: 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9d7e...16ea`](https://etherscan.io/address/0x9d7e01f6f4dcfbe3df783d18326e4d1fd8be16ea) |
| **Network** | Ethereum |
| **Price** | $0.00001905 |
| **24h Volume** | $39.3K |
| **Liquidity** | $11.8K |
| **Volume / Liquidity** | 3.3× |
| **Token Age** | 3d |
| **Top-10 Holders** | 27.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 152 buys / 144 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xf15a973c54d71dcd3cca1dc1a921a7cbee55fc6f37db990b9ac6a3dd60d80308)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wojak-eth-8118)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
