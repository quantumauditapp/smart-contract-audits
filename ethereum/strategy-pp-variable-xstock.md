---
token: Strategy PP Variable xStock
ticker: STRCX
network: ethereum
risk_score: 9
status: low
date: 2026-10-31
---

# Strategy PP Variable xStock (STRCX) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/strategy-pp-variable-xstock-eth)

---

## Audit Summary

The protocol implements an upgradeable ERC-20 token with advanced fee and delegation features. While the architecture follows standard OpenZeppelin patterns, the contract grants significant centralized control to privileged roles, including the ability to mint tokens, pause transfers, and perform delegated transfers on behalf of users. Users should be aware that these administrative powers represent a high degree of centralization risk.

> **Final Recommendation:** The protocol should implement a timelock contract for all administrative actions, particularly those involving minting or changing fee parameters, to provide transparency and a window for users to react. Additionally, consider reducing the scope of the 'delegateWhitelist' role to minimize the impact of a potential compromise of these addresses.

Regularly audit the addresses assigned to privileged roles to ensure they remain secure and under the control of the intended multisig. Ensure that the 'sanctionsList' contract is maintained by a reputable entity to prevent arbitrary blocking of legitimate users.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract utilizes a robust UUPS/Transparent proxy pattern for upgradeability and standard ERC-20 compliance. 7.1 Architecture: Modular design separating logic from state. 7.2 Code Security… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic: The token supply is elastic, controlled by the minter and multiplier updater roles. 7.5 Governance: Administrative control is held by a multisig, providing a layer of protection against… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: The contract uses a standard Transparent Proxy pattern managed by a dedicated ProxyAdmin. Upgrades are controlled by a multisig, ensuring that changes to the implementation require… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 2-of-3 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 93.1% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 7 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Informational · Status: Unresolved)*

Privileged roles (minter, multiplier updater, owner) can mint new tokens, which dilutes the value of existing holdings. This is a significant centralization risk as the total supply is not fixed.

**Recommendation:** Implement a timelock for minting operations and define clear, transparent rules for when and why new tokens are minted.


### `CP-02` — Privileged Balance Manipulation  *(Severity: Informational · Status: Unresolved)*

The 'delegatedTransfer' function allows addresses on the 'delegateWhitelist' to move tokens from any user's account. This is a high-risk function that could lead to total loss of funds if a whitelisted address is compromised.

**Recommendation:** Restrict the use of 'delegatedTransfer' to only essential services and implement strict monitoring for any activity involving this function.


### `CP-04` — Centralized Pause Control  *(Severity: Informational · Status: Unresolved)*

The 'pauser' role can halt all token transfers at any time. This prevents users from moving their assets, which could be used to freeze funds during an emergency or maliciously.

**Recommendation:** Limit the pause functionality to specific emergency scenarios and ensure the pauser role is held by a secure, multi-signature wallet.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.4% of supply. What remains: 25.6% in wallets, 73.8% in other contracts. 4,944 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Strategy PP Variable xStock (STRCX), market cap $151M, rank #207. Its owner (0x4975…3a65) controls 119 issuer-backed coins CoinGecko lists on ethereum, $949M together, among them MicroStrategy xStock, Circle xStock, SpaceX xStock: one issuer's programme, read on-chain. 4,944 holders. Verified by: CoinGecko, issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $137K (DexScreener, all pools). 24h trading volume $6.8M (CoinGecko, all markets, daily snapshot). 24h trading volume $292K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: a 2-of-3 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $137K of DEX liquidity across 7 pools. Launch: 163 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1aad...77f3`](https://etherscan.io/address/0x1aad217b8f78dba5e6693460e8470f8b1a3977f3) |
| **Network** | Ethereum |
| **Price** | $99.4000 |
| **24h Volume** | $268.1K |
| **Liquidity** | $115.1K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 99.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 118 buys / 125 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xabc4aca2bbede9a98563f7660e126272f1a86137ba07c655e4d4ec2245a933bf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/strategy-pp-variable-xstock-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
