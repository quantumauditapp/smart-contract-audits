---
token: ConwayResearch
ticker: CONWAY
network: base
risk_score: 72
status: high
date: 2026-10-03
---

# ConwayResearch (CONWAY) — Smart Contract Security Analysis | Base

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/conwayresearch-base)

---

## Audit Summary

The ClankerToken is an ERC-20 token with additional features for cross-chain operations and governance. The audit identified significant centralized control points, specifically concerning token minting and burning, which are controlled by a `SuperchainTokenBridge` address. An `_admin` role also manages metadata. These centralized controls introduce high technical and economic risks if the controlling addresses are compromised.

> **Final Recommendation:** It is crucial to implement robust security measures for the `SuperchainTokenBridge` address, as it holds critical power over token supply and individual balances. Consider multi-signature wallets or time-locks for these sensitive operations to mitigate the risk of a single point of failure. Additionally, ensure the `_admin` role is managed securely, potentially through a DAO or a multi-signature setup, to prevent unauthorized changes to administrative parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The ClankerToken implements standard ERC-20 functionality robustly, inheriting from OpenZeppelin contracts and including ERC-20Permit and ERC20Votes for enhanced usability and governance. However… |
| **Governance / Economics** | 2/10 | High | The token incorporates `ERC20Votes`, enabling decentralized governance participation through voting power delegation. However, the `SuperchainTokenBridge` has the ability to mint an arbitrary amount… |
| **Upgrades** | 5/10 | Medium | The contract is not designed with an upgrade mechanism, which eliminates risks associated with upgradeability patterns such as proxy implementation bugs or insecure upgrade paths. The lack of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x63d2…3496 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — The `SuperchainTokenBridge` can create new tokens.  *(Severity: Informational · Status: Unresolved)*

The `crosschainMint` function allows the `SuperchainTokenBridge` to create an unlimited number of new ClankerTokens and assign them to any address. This means the `SuperchainTokenBridge` can increase the total supply of tokens at will, which could dilute the value of tokens held by existing holders. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Token holders should be aware that the `SuperchainTokenBridge` has the power to mint new tokens. It is critical that the `SuperchainTokenBridge` address is secured with the highest level of protection, such as a robust multi-signature wallet or a decentralized autonomous organization (DAO) governance, to prevent unauthorized minting.


### `CP-02` — The `SuperchainTokenBridge` can burn tokens from any holder's balance.  *(Severity: Informational · Status: Unresolved)*

The `crosschainBurn` function allows the `SuperchainTokenBridge` to remove any amount of ClankerTokens from any token holder's balance without their permission. This means the `SuperchainTokenBridge` can arbitrarily reduce the token holdings of any user, posing a significant risk to individual token ownership. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Token holders should understand that the `SuperchainTokenBridge` has the ability to burn tokens from any account. Ensuring the `SuperchainTokenBridge` is controlled by a highly secure and transparent mechanism, like a multi-signature wallet with multiple trusted signers or a DAO, is paramount to protect token holders' assets from unauthorized burning.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 58.7% of supply. What remains: 10.4% in wallets, 48.3% in other contracts. 4,401 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,401 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $159K (DexScreener, all pools). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $159K of DEX liquidity across 18 pools. Launch: 242 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x86cd...ab07`](https://basescan.org/address/0x86cdd90bc48f7b5a866feaaf5023b8802dc2ab07) |
| **Network** | Base |
| **Price** | $0.0000032 |
| **24h Volume** | $1.06M |
| **Liquidity** | $157.0K |
| **Volume / Liquidity** | 6.7× |
| **Token Age** | 8mo |
| **Top-10 Holders** | 58.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1746 buys / 3857 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xae11897d5a77fe094f4745b5e1992b3bc331ff659e959ae8789b5e92b9d5b921)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/conwayresearch-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*
