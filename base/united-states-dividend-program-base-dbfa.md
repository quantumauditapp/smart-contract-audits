---
token: United States Dividend Program🔥
ticker: USDP
network: base
risk_score: 57
status: medium
date: 2026-10-22
---

# United States Dividend Program🔥 (USDP) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-dividend-program-base-dbfa)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance, voting, and vesting capabilities. The architecture is robust, leveraging OpenZeppelin standards for core functionality. However, the contract grants significant centralized control to the owner, including the ability to mint tokens and halt transfers, which introduces notable trust requirements for token holders.

> **Final Recommendation:** To improve security, consider transitioning ownership to a decentralized multi-signature wallet or a DAO governance contract to mitigate single-point-of-failure risks. Additionally, implementing a timelock on privileged functions like updateMintRate would provide transparency and allow the community to react to significant economic changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, EIP-712, and voting mechanisms. 7.1 Architecture is modular, and 7.2 Code Security is high due to standard implementations. 7.3… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the owner's ability to influence supply and liquidity. The owner can mint tokens up to a 2% annual cap via updateMintRate, which impacts token… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable, providing certainty to users regarding the contract's behavior. No upgrade-related risks exist for this… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Control  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to increase the total supply of tokens through the updateMintRate and release functions. This allows the owner to dilute existing token holders at their discretion, provided they stay within the 2% annual inflation limit.

**Recommendation:** Restrict minting capabilities to a multi-signature wallet or replace the owner with a decentralized governance contract to ensure community oversight of supply changes.


### `CP-05` — Centralized Transfer Control  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch via the lockPool and unlockPool functions. This allows the owner to unilaterally halt or enable token transfers, effectively freezing user assets or restricting liquidity at will.

**Recommendation:** Remove the ability to pause transfers or implement a timelock mechanism that requires a notice period before any changes to transfer rules can take effect.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 3,117 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,117 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $98K (DexScreener, all pools). 24h trading volume $219K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.1951 — it does not hold a peg. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $98K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xff4c...3bad`](https://basescan.org/address/0xff4c745237845cc07c34c3ac87acb16349243bad) |
| **Network** | Base |
| **Price** | $0.1951 |
| **24h Volume** | $219.3K |
| **Liquidity** | $97.8K |
| **Volume / Liquidity** | 2.2× |
| **Token Age** | 16h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3068 buys / 2940 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xce9d8068f34929fa27e49087e3aae24576ca295e13d76e176f4add919acaf08f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-dividend-program-base-dbfa)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
