---
token: Papertrade
ticker: PAPER
network: base
risk_score: 56
status: medium
date: 2026-10-11
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base)

---

## Audit Summary

The ClankerToken contract is an ERC-20 token with additional functionalities for cross-chain operations and administrative controls. While it implements standard token features, the audit identified significant centralization risks. Specifically, a designated 'SuperchainTokenBridge' address has the power to mint new tokens and burn tokens from any holder's balance, posing a high risk to token holders regarding dilution and arbitrary fund loss. An 'admin' address also controls metadata updates and can transfer its own administrative role.

> **Final Recommendation:** Token holders should be fully aware of the extensive centralized control over the ClankerToken supply and individual balances. The `Predeploys.SUPERCHAIN_TOKEN_BRIDGE` address holds critical power to mint new tokens and burn existing ones from any account. It is essential to understand the operational policies, security measures, and governance mechanisms surrounding this controlling address and the 'admin' address to assess the associated risks.

For the protocol developers, consider implementing multi-signature controls or time-locks for highly privileged functions like `crosschainMint` and `crosschainBurn` to reduce the risk of a single point of compromise or malicious action. Enhance transparency by clearly documenting the roles and responsibilities of the `SUPERCHAIN_TOKEN_BRIDGE` and `admin` addresses, including any off-chain governance processes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The ClankerToken contract implements the ERC-20 standard, providing standard token functionalities like transfer and balance checks (7.1 Architecture). The code includes privileged functions such as… |
| **Governance / Economics** | 1/10 | High | The economic model of the ClankerToken is subject to significant centralized control (7.4 Economic). The `Predeploys.SUPERCHAIN_TOKEN_BRIDGE` address has the power to mint an arbitrary amount of new… |
| **Upgrades** | 5/10 | Medium | The ClankerToken contract is not designed as an upgradeable proxy, meaning its logic cannot be changed after deployment (7.7 Upgrades). This provides certainty regarding the immutability of the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 7 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Centralized Minting Capability  *(Severity: Informational · Status: Unresolved)*

The `crosschainMint` function allows a specific controller, identified as `Predeploys.SUPERCHAIN_TOKEN_BRIDGE`, to create new Clanker tokens at any time. This means the total supply of tokens can be increased without limit. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Token holders should be aware that the value of their tokens could be diluted if the `SUPERCHAIN_TOKEN_BRIDGE` address mints a large number of new tokens. Transparency regarding minting policies and operations by the controlling entity is crucial.


### `CP-02` — Centralized Token Burning Authority  *(Severity: Informational · Status: Unresolved)*

The `crosschainBurn` function grants the `Predeploys.SUPERCHAIN_TOKEN_BRIDGE` address the ability to burn (destroy) Clanker tokens from any holder's wallet. This means tokens can be removed from your balance without your consent. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Token holders face a risk of arbitrary loss of funds if the `SUPERCHAIN_TOKEN_BRIDGE` address misuses its power to burn tokens. It is important to understand the operational policies and security measures surrounding this controlling address.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 5,247 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,247 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $7.1M (DexScreener, all pools). 24h trading volume $43.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $7.1M of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5f8f...ab07`](https://basescan.org/address/0x5f8fc6a725de67e74ec489819d8848c1545aab07) |
| **Network** | Base |
| **Price** | $0.00007143 |
| **24h Volume** | $43.32M |
| **Liquidity** | $7.07M |
| **Volume / Liquidity** | 6.1× |
| **Token Age** | 18h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2955 buys / 2759 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xad5ed74049a00ddf2a5920c3341db186831f493e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
