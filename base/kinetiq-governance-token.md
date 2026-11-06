---
token: Kinetiq Governance Token
ticker: KNTQ
network: base
risk_score: 57
status: medium
date: 2026-11-06
---

# Kinetiq Governance Token (KNTQ) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kinetiq-governance-token-base)

---

## Audit Summary

The FactoryBurnMintERC20 contract is a standard burnable and mintable ERC-20 token implementation. The architecture relies on a centralized owner to manage minting and burning roles. While the code is clean and follows standard OpenZeppelin patterns, the ability for privileged addresses to mint tokens represents a significant economic risk to token holders.

> **Final Recommendation:** The protocol should implement a timelock controller for all privileged minting and role management functions to provide transparency and a window for community response. Additionally, consider setting a permanent, non-upgradable max supply to mitigate long-term inflation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited libraries for ERC-20 and Ownable2Step functionality. 7.1 Architecture is modular, and 7.2 Code Security is robust with no reentrancy or overflow vulnerabilities.… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risk is primarily driven by the minting capability, which allows for supply inflation. 7.5 Governance is centralized under a multisig wallet, providing a balance between security and… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not supported as this is a non-proxy contract. 7.8 Operations are handled via standard ownership transfer procedures. The lack of upgradeability ensures immutability of the core… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows addresses with the 'minter' role to create new tokens at will. This can lead to the dilution of existing token holders' value if the minter role is compromised or misused.

**Recommendation:** Restrict the minting capability to a multi-signature wallet or a decentralized governance contract. Implement a timelock on the grantMintRole function to prevent sudden changes in administrative access.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x7185…02ab — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.9% of supply. What remains: 6.5% in wallets, 93.5% in other contracts. 42 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

42 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $808K (DexScreener, all pools). 24h trading volume $1.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-4 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $808K of DEX liquidity across 4 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb801...e7dd`](https://basescan.org/address/0xb80194e3868511b8f43e1d5d6e255cd9e7c3e7dd) |
| **Network** | Base |
| **Price** | $0.4423 |
| **24h Volume** | $1.51M |
| **Liquidity** | $807.7K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 5h |
| **Top-10 Holders** | 99.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2891 buys / 2833 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x2acfe5952ea0e78c73ea7ca5d709c3c1c13ab661)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kinetiq-governance-token-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
