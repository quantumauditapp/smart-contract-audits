---
token: GRAIL
ticker: GRAIL
network: ethereum
risk_score: 50
status: medium
date: 2026-11-05
---

# GRAIL (GRAIL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grail-eth)

---

## Audit Summary

GrailToken is an EIP-1167 minimal clone implementation. The contract features centralized control via a launchpad address, which holds significant power over token supply and transfer mechanics. While the code is standard, the centralization of administrative functions poses a risk to token holders.

> **Final Recommendation:** Investors should be aware that the launchpad address retains significant control over the token's economic parameters. We recommend transitioning the launchpad role to a multi-signature wallet or a decentralized governance contract to mitigate the risk of centralized abuse.

Ensure that the launchpad address is secured with robust key management practices, as any compromise of this address could lead to unauthorized minting or manipulation of transfer rules.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a standard EIP-1167 minimal clone pattern, ensuring immutable logic. 7.1 Architecture is sound for a token deployment, and 7.2 Code Security reflects standard ERC-20… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The launchpad address has the authority to mint tokens and modify transfer fees, which directly impacts holder value. These powers are… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are not applicable as the contract is an EIP-1167 clone. The implementation logic is fixed at deployment, preventing future logic changes. 7.8 Operations are stable due to this… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The initialize function allows the launchpad address to mint an arbitrary amount of tokens. This can lead to significant dilution of existing token holders if misused.

**Recommendation:** Implement a hard cap on the total supply or require a multi-signature approval process for any minting actions.


### `CP-07` — Dynamic Transfer Fee Control  *(Severity: Medium · Status: Unresolved)*

The launchpad address has the authority to change transfer fees via the initialize function, which can be used to restrict liquidity or extract value from users.

**Recommendation:** Set a maximum fee threshold in the contract to prevent excessive charges and provide transparency to users.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x6bd1…aeef — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-08` — Administrative Control Over Limits  *(Severity: Low · Status: Unresolved)*

The launchpad address can modify transaction and wallet limits, potentially freezing user assets or restricting trading activity.

**Recommendation:** Document these limits clearly and consider making them immutable after a set period to increase user confidence.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 85.3% of supply. Of that, 67.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 10.5% in wallets, 7.4% in other contracts. The deployer/owner wallet itself holds 1.1%. 91 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

91 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $45K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $13K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0d8e...d26a`](https://etherscan.io/address/0x0d8e9046a6a6e24f5c0ff86303940b270208d26a) |
| **Network** | Ethereum |
| **Price** | $0.00001416 |
| **24h Volume** | $44.6K |
| **Liquidity** | $13.1K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 19h |
| **Top-10 Holders** | 85.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 207 buys / 138 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x5309a9f44498051d27d1a584bbd7cb32c62030f9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grail-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
