---
token: Tectum Emission Token
ticker: TET
network: ethereum
risk_score: 70
status: high
date: 2026-10-21
---

# Tectum Emission Token (TET) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tectum-emission-token-eth)

---

## Audit Summary

The Tettoken contract is a standard ERC-20 implementation with additional administrative functions for supply management. The contract relies on a centralized owner to manage total supply, which introduces significant trust requirements. The code follows standard patterns but lacks modern security features like reentrancy guards or circuit breakers.

> **Final Recommendation:** Token holders should be aware that the owner possesses the authority to mint new tokens, which may dilute existing holdings. We recommend that the project team considers transitioning to a multi-signature wallet for the owner address to mitigate the risk of a single compromised key.

Furthermore, implementing a timelock on the privileged functions (tetwrite, issue, redeem) would provide transparency and allow the community time to react to significant changes in the token supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements standard ERC-20 functionality including transfer and approval mechanisms. 7.1 Architecture is straightforward, utilizing a single-contract design. 7.2 Code Security is… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance are entirely centralized under the owner address. The owner has the unilateral ability to mint or burn tokens, directly impacting the token's value and scarcity. This… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable once deployed, which provides certainty to users regarding the contract's behavior. 7.8 Operations are limited to… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 3 Informational_

### `CP-01` — Centralized Supply Control  *(Severity: Medium · Status: Unresolved)*

The owner of the contract has the ability to mint new tokens and burn existing ones via the tetwrite, issue, and redeem functions. This allows the controller to arbitrarily increase the total supply, which dilutes the value of tokens held by other users.

**Recommendation:** Consider renouncing ownership if the supply is intended to be fixed, or implement a multi-signature wallet or a timelock mechanism to require community consensus before supply changes are executed.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x4302…f840 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $359K (DexScreener, all pools). 24h trading volume $113K (CoinGecko, all markets, daily snapshot). 24h trading volume $37K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $45.03 on 2024-01-06; the price is now 99.1845% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 42.4% of supply. Of that, 4.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 38.1% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 9.1%. 14,426 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Tectum (TET), market cap $4M, rank #1887. 14,426 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $359K of DEX liquidity across 1 pools. Launch: 1206 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x68a4...ca0a`](https://etherscan.io/address/0x68a47fe1cf42eba4a030a10cd4d6a1031ca3ca0a) |
| **Network** | Ethereum |
| **Price** | $0.4222 |
| **24h Volume** | $36.7K |
| **Liquidity** | $359.2K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 42.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 68 buys / 51 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xefdf4dfc4e817197851266acf0082a80dab18b24)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tectum-emission-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
