---
token: Zero Gap
ticker: ZGAP
network: ethereum
risk_score: 49
status: medium
date: 2026-10-25
---

# Zero Gap (ZGAP) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zero-gap-eth)

---

## Audit Summary

The PangeaOFTV2 contract is a LayerZero-enabled Omnichain Fungible Token. The architecture follows standard OFT patterns, allowing cross-chain transfers via mint/burn mechanisms. While the contract is well-structured, it contains centralized administrative roles that can influence token supply and metadata, which requires careful key management.

> **Final Recommendation:** The protocol should ensure that the 'supplyReporter' and 'metadataAuthority' roles are held by multi-signature wallets or decentralized governance contracts to mitigate the risk of single-point-of-failure. Regular monitoring of supply changes is recommended to ensure transparency for token holders.

Given the centralized nature of the administrative roles, we recommend implementing a timelock for any significant changes to the contract state, particularly for roles that can influence the token supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a robust LayerZero OFT implementation, ensuring standard cross-chain interoperability. 7.1 Architecture is modular and follows established patterns for cross-chain messaging.… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance risks are centered on the 'supplyReporter' and 'metadataAuthority' roles. These roles have the power to influence token supply and metadata, which could impact market… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not explicitly implemented via proxy patterns in this contract, reducing complexity. 7.8 Operations are straightforward, relying on standard ownership management. The lack of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 55.4% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The functions 'send', 'lzReceive', and 'reportSupply' allow privileged addresses (the LayerZero endpoint or the 'supplyReporter') to mint tokens or alter the reported supply. This grants these entities the ability to dilute existing token holders or manipulate the circulating supply.

**Recommendation:** Restrict the 'supplyReporter' role to a multi-signature wallet or a DAO-controlled contract. Ensure that all supply changes are logged and publicly verifiable to maintain trust with the community.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0xa6f3…e168 — holds 55.4% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 15.1% of supply. What remains: 5.2% in wallets, 9.9% in other contracts. 87 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

87 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $30K (DexScreener, all pools). 24h trading volume $106K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $30K of DEX liquidity across 4 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdba1...96ea`](https://etherscan.io/address/0xdba134ad399e15d9175ce6bc97beca7001fb96ea) |
| **Network** | Ethereum |
| **Price** | $0.00009017 |
| **24h Volume** | $105.8K |
| **Liquidity** | $30.0K |
| **Volume / Liquidity** | 3.5× |
| **Token Age** | 7h |
| **Top-10 Holders** | 15.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 347 buys / 282 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x53bf62e3920ef10e593c8a1b24a091916ea00d076913a38b9767b3903a57c7c1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zero-gap-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
