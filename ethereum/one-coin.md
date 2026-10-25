---
token: one coin
ticker: ONECOIN
network: ethereum
risk_score: 71
status: high
date: 2026-10-25
---

# one coin (ONECOIN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 71/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/one-coin-eth)

---

## Audit Summary

The PangeaOFTV2 contract implements an Omnichain Fungible Token (OFT) standard. The architecture relies on LayerZero for cross-chain messaging and utilizes specific roles for metadata management and supply reporting. While the code follows standard patterns, the presence of privileged minting capabilities requires careful monitoring of the assigned roles.

> **Final Recommendation:** The protocol should implement a multi-signature wallet or a time-locked governance contract for the 'supplyReporter' and 'metadataAuthority' roles to mitigate the risk of unauthorized supply changes. Continuous monitoring of the 'reportSupply' function is recommended to ensure that any changes to the total supply are transparently communicated to the community.

Users and integrators should verify the addresses assigned to privileged roles periodically. Since the contract is immutable, ensure that all operational procedures for role management are documented and audited before execution.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract architecture (7.1) follows the established LayerZero OFT standard, ensuring robust cross-chain interoperability. Code security (7.2) is high, utilizing modern Solidity practices and… |
| **Governance / Economics** | 4/10 | Medium | Economic parameters (7.4) are centralized, with specific roles controlling supply reporting and metadata. Governance (7.5) is currently managed by an owner contract, which allows for administrative… |
| **Upgrades** | 4/10 | Medium | The contract is not currently deployed as a proxy (7.7), meaning the logic is immutable. This eliminates risks associated with malicious implementation upgrades. Future changes would require a full… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Privileged Minting Capability  *(Severity: Medium · Status: Unresolved)*

The functions send, lzReceiveSimulate, lzReceive, and reportSupply allow privileged addresses (endpoint or supplyReporter) to increase the total token supply. This action can dilute the value of existing holdings if performed without community consensus.

**Recommendation:** Restrict the 'supplyReporter' role to a multi-signature wallet or a decentralized governance contract. Implement event monitoring to alert the community whenever the total supply is updated via these functions.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xebbd…4593 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 28.1% of supply. What remains: 5.7% in wallets, 22.5% in other contracts. 83 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

83 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $30K (DexScreener, all pools). 24h trading volume $199K (DexScreener, all pools).

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
| **Contract** | [`0x373c...f6ea`](https://etherscan.io/address/0x373c863e4c34db35b58c98dd15a018e1ab53f6ea) |
| **Network** | Ethereum |
| **Price** | $0.00008871 |
| **24h Volume** | $198.7K |
| **Liquidity** | $29.6K |
| **Volume / Liquidity** | 6.7× |
| **Token Age** | 2h |
| **Top-10 Holders** | 28.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 398 buys / 391 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x8795f5763781a2842299c1e59225f32864114f561068f4943c9b3d1b105a1ff4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/one-coin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
