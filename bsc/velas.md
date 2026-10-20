---
token: Velas
ticker: VLX
network: bsc
risk_score: 77
status: high
date: 2026-10-15
---

# Velas (VLX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 77/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/velas-bsc)

---

## Audit Summary

The ERC677BridgeToken contract provides standard ERC-20 functionality with additional features for bridging and minting. The contract owner retains significant control, including the ability to mint new tokens and directly manipulate token balances of other holders. These capabilities introduce substantial centralization risks, as a compromised or malicious owner could dilute existing token holders or arbitrarily move funds.

> **Final Recommendation:** Given the significant power vested in the contract owner, it is paramount to ensure the owner's private key is secured with the highest possible standards, ideally through a robust multi-signature wallet. Implement strict operational procedures for executing privileged functions, especially `mint` and `transferAndCall`, to prevent unauthorized or erroneous actions. Consider implementing a timelock for critical operations to provide a window for community review and reaction.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements the ERC-20 and ERC-677 standards, providing robust token transfer mechanisms (7.2 Code Security). It includes owner-restricted functions for managing token supply and bridge… |
| **Governance / Economics** | 2/10 | High | The contract's economic model is highly centralized, with the owner possessing extensive control over the token supply and individual balances (7.4 Economic). The owner, identified as an… |
| **Upgrades** | 4/10 | Medium | The contract is not implemented as a proxy and does not include any upgrade mechanisms (7.7 Upgrades). This means the contract's logic is immutable once deployed, eliminating risks associated with… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 0.7% — DxLock |
| **Top-1 Unlocked Holder** | ⚠️ 84.9% |
| **Top-3 Unlocked** | ⚠️ 98.8% |

## Security Findings

_🟠 1 High · 🟡 3 Medium · ⚪ 3 Informational_

### `CP-02` — Owner Can Directly Manipulate Any Holder's Tokens  *(Severity: High · Status: Unresolved)*

The contract owner possesses a highly powerful capability through the `transferAndCall(address,uint256,bytes)` function. The static analysis indicates this function allows the owner to directly modify the token balances of any holder, meaning the owner could move tokens out of any address or even burn them without the holder's consent. This represents a critical centralization risk.

**Recommendation:** This capability gives the owner absolute control over all token balances. Token holders must understand that their tokens are subject to the owner's discretion. It is essential that the owner's private key is extremely well-protected, ideally by a multi-signature wallet with a strong governance process, to prevent malicious or accidental manipulation of funds.


### `CP-01` — Owner Can Create New Tokens  *(Severity: Medium · Status: Unresolved)*

The contract owner has the ability to create an unlimited number of new tokens using the `mint(address,uint256)` function. This means the owner can increase the total supply of tokens at any time, which could dilute the value of existing tokens held by others.

**Recommendation:** Token holders should be aware that the owner can inflate the token supply. It is crucial that the owner's address is controlled by a highly secure entity, such as a multi-signature wallet, and that there are clear policies governing when and how new tokens can be minted.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.7% still sits in DxLock, but that lock expired on 21 Nov 2022 — its owner can withdraw it at any moment. 99.3% is held, unlocked, by 5 address(es) other than the owner/deployer. One of them — a wallet, 0x0424…cb74 — holds 84.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $24K (DexScreener, all pools). 24h trading volume $80K (CoinGecko, all markets, daily snapshot). 24h trading volume $160K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.569 on 2022-01-04; the price is now 99.992% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 66.6% of supply. Of that, 35.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 21.8% in wallets, 9.3% in other contracts. 46,648 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Velas (VLX), rank #5394. 46,648 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $24K of DEX liquidity across 10 pools. Launch: 1864 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe9c8...45fc`](https://bscscan.com/address/0xe9c803f48dffe50180bd5b01dc04da939e3445fc) |
| **Network** | BNB Chain |
| **Price** | $0.00005362 |
| **24h Volume** | $159.7K |
| **Liquidity** | $23.7K |
| **Volume / Liquidity** | 6.8× |
| **Token Age** | 5y |
| **Top-10 Holders** | 66.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1134 buys / 705 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x48d807e5cb92617953a88cce78dcf31012f4d6b6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/velas-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
