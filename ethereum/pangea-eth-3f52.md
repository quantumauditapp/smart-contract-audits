---
token: Pangea
ticker: PANGEA
network: ethereum
risk_score: 73
status: high
date: 2026-10-21
---

# Pangea (PANGEA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 73/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pangea-eth-3f52)

---

## Audit Summary

The PangeaOFT contract implements an Omnichain Fungible Token (OFT) standard. The architecture relies on LayerZero for cross-chain messaging and includes specific roles for metadata management and supply reporting. The protocol exhibits a centralized control structure where specific addresses hold the power to modify metadata and report supply, which impacts the total supply of the token.

> **Final Recommendation:** It is recommended to transition the supplyReporter and metadataAuthority roles to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single compromised key. Ensure that the addresses assigned to these roles are monitored for suspicious activity.

Regularly audit the LayerZero endpoint configurations and enforced options to ensure that cross-chain parameters remain within expected bounds. Maintain transparency regarding the supply reporting process to ensure token holders are aware of any changes to the total supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract utilizes the robust LayerZero OFT standard, ensuring standard-compliant cross-chain transfers. Coverage includes 7.1 Architecture (OFT standard), 7.2 Code Security (standard library… |
| **Governance / Economics** | 3/10 | High | Governance is centralized through specific roles: metadataAuthority and supplyReporter. 7.4 Economic and 7.5 Governance coverage indicates that these roles can influence token supply and metadata.… |
| **Upgrades** | 4/10 | Medium | The contract is not currently deployed as a proxy, meaning 7.7 Upgrades risk is minimal. Logic is immutable unless the owner deploys a new contract and migrates state. 7.8 Operations are handled via… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The protocol grants specific privileged addresses (supplyReporter and LayerZero endpoint) the ability to mint new tokens or report supply changes. This allows these controllers to potentially dilute the value of existing holdings if the authority is misused or compromised.

**Recommendation:** Implement a multi-signature wallet for the supplyReporter role and establish clear, time-locked governance procedures for any supply adjustments to prevent unilateral actions.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x3b4b…bf80 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 65.1% of supply. What remains: 14.5% in wallets, 50.6% in other contracts. 100 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

100 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $71K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3379...36ea`](https://etherscan.io/address/0x3379bb6c7c0d743b36fed2909e89ab29008c36ea) |
| **Network** | Ethereum |
| **Price** | $0.0000381 |
| **24h Volume** | $70.6K |
| **Liquidity** | $18.4K |
| **Volume / Liquidity** | 3.8× |
| **Token Age** | 6h |
| **Top-10 Holders** | 65.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 365 buys / 260 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xb140e81dea9550637676605ad29d1f2336a63285e52f65354a46a150897fe5ce)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pangea-eth-3f52)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
