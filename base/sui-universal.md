---
token: Sui (Universal)
ticker: USUI
network: base
risk_score: 58
status: medium
date: 2026-10-25
---

# Sui (Universal) (USUI) — Smart Contract Security Analysis | Base

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sui-universal-base)

---

## Audit Summary

The WrappedAssetV2 contract is a standard ERC-20 implementation utilizing OpenZeppelin's upgradeable libraries. It features centralized minting capabilities and a blacklist mechanism controlled by specific roles. The architecture is robust, leveraging battle-tested libraries for access control and proxy management.

> **Final Recommendation:** Maintain the current multisig threshold and ensure that the keys are stored in geographically distributed hardware security modules. Regularly audit the list of addresses granted the 'merchant_controller' and 'RESPONDER_ROLE' to ensure that only authorized entities retain these sensitive permissions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract utilizes standard OpenZeppelin upgradeable patterns, ensuring 7.1 Architecture and 7.2 Code Security compliance. 7.3 Access Control is strictly enforced via AccessControlUpgradeable… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance risks are centered on the centralized control of the minting and blacklisting functions. While necessary for a wrapped asset, these powers allow the controller to… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are managed via a BeaconProxy pattern, which is a secure and standard approach for multi-contract deployments. 7.8 Operations are supported by the DefaultAdminRules, which include a… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 69.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a wallet, 0xfa2b…52bb — holds 69.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — a 2-of-4 multisig — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 36.8% of supply. What remains: 10.1% in wallets, 26.7% in other contracts. 64,686 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Wrapped SUI (Universal) (USUI). 64,686 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $41K (DexScreener, all pools). 24h trading volume $24K (CoinGecko, all markets, daily snapshot). 24h trading volume $66K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Wrapped-Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 2-of-4 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $41K of DEX liquidity across 11 pools. Launch: 709 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb050...6ea4`](https://basescan.org/address/0xb0505e5a99abd03d94a1169e638b78edfed26ea4) |
| **Network** | Base |
| **Price** | $0.9167 |
| **24h Volume** | $65.8K |
| **Liquidity** | $40.6K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 36.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 504 buys / 561 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x5c45b0f48c326f79b56709d8f63ce2bee7697106)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sui-universal-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
