---
token: AgentID
ticker: AGI
network: ethereum
risk_score: 67
status: high
date: 2026-11-05
---

# AgentID (AGI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/agentid-eth)

---

## Audit Summary

The AGIToken contract implements a standard ERC-20 token with significant centralized control mechanisms. The 'minter' role holds extensive power to manipulate supply, freeze user assets, and restrict transferability. While the code follows standard patterns for minting and burning, the lack of timelocks or multi-signature requirements for these privileged functions introduces substantial counterparty risk for token holders.

> **Final Recommendation:** It is strongly recommended to transition the 'minter' role to a multi-signature wallet or a decentralized DAO contract to mitigate the risk of a single point of failure. Additionally, implement a timelock for sensitive administrative actions to provide transparency and allow the community to react to significant changes in tokenomics or access rules.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes standard OpenZeppelin-like ERC-20 logic with robust implementation of core token standards. 7.1 Architecture is straightforward, though 7.2 Code Security is hampered by the… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance risks are high due to the centralized 'minter' role. This entity can unilaterally dilute supply via minting or seize assets via burnFromHolder. There are no… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable once deployed, which provides certainty but prevents patching of the identified centralized control issues.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.8% (≈ permanent lock) |
| **LP Locked** | 99.8% — Null Address |

## Security Findings

_🟠 1 High · 🟡 4 Medium · ⚪ 6 Informational_

### `CP-02` — Unauthorized Asset Seizure  *(Severity: High · Status: Unresolved)*

The minter role has the ability to burn tokens directly from any user's wallet using the burnFromHolder function, effectively allowing for the seizure of user assets.

**Recommendation:** Remove the ability for the minter to burn tokens from arbitrary user addresses, or restrict this function to only operate on tokens explicitly approved by the user.


### `CD-01` — Stuck ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract includes a receive function that accepts ETH, but there is no mechanism to withdraw or recover these funds, leading to permanent loss of any sent ETH.

**Recommendation:** Remove the receive function if the contract is not intended to hold ETH, or add a function to allow the owner to withdraw accidentally sent funds.


### `CP-01` — Centralized Minting Capability  *(Severity: Medium · Status: Unresolved)*

The minter role can increase the total supply of tokens at any time, which dilutes the value of existing holdings for all token holders.

**Recommendation:** Restrict minting to a capped schedule or require a multi-signature approval process for any new supply issuance.


### `CP-05` — Transferability Control Switch  *(Severity: Medium · Status: Unresolved)*

The minter can toggle a global switch that prevents all token transfers, effectively locking all liquidity in the ecosystem.

**Recommendation:** Remove the global transfer lock or implement a community-governed voting mechanism to trigger such a state change.


### `CP-06` — Blacklisting Capability  *(Severity: Medium · Status: Unresolved)*

The minter can add specific addresses to a blacklist, preventing those users from moving or selling their tokens.

**Recommendation:** Limit the blacklist functionality to only be used for regulatory compliance and ensure there is a transparent process for appeals.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 41.4% of supply. Of that, 31.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 7.6% in wallets, 2.0% in other contracts. 1,272 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,272 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.8% of the pool's LP is burned or time-locked. 99.8% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $36K (DexScreener, all pools). 24h trading volume $86K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 1% on buy, 1% on sell. Market: $36K of DEX liquidity across 1 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbf01...a461`](https://etherscan.io/address/0xbf01c3ef1bc368288067d4ac49ba9b147de3a461) |
| **Network** | Ethereum |
| **Price** | $0.0002298 |
| **24h Volume** | $85.5K |
| **Liquidity** | $36.4K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 2d |
| **Top-10 Holders** | 41.4% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 450 buys / 788 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x4907d3da4c1b253ac1d8400944733d52348bb863)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/agentid-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
