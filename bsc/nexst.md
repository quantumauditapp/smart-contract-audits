---
token: NEXST
ticker: NXT
network: bsc
risk_score: 66
status: high
date: 2026-10-16
---

# NEXST (NXT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nexst-bsc)

---

## Audit Summary

The NEXST token contract implements standard ERC-20 functionality with additional features like pausing, blacklisting, and minting. It leverages OpenZeppelin's AccessControl and Ownable for managing permissions. The contract exhibits a high degree of centralized control, with specific roles or the owner able to mint new tokens, pause all transfers, and blacklist individual addresses. These centralized powers, while managed by a multisig owner, introduce potential economic and operational risks.

> **Final Recommendation:** It is crucial for token holders to understand the significant centralized control inherent in the NEXST token contract. The project team should clearly communicate the operational policies and security measures surrounding the multisig owner and the `MINTER_ROLE` to ensure transparency. Consider implementing a timelock for critical administrative actions like `minting` or `pausing` to provide a window for community review and reaction. Additionally, explore options for progressive decentralization of these powers over time, such as integrating a community governance mechanism for key decisions, to reduce reliance on a centralized entity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The NEXST token contract is built upon robust OpenZeppelin standards, inheriting from ERC20, Pausable, ERC20Capped, ERC20Burnable, and AccessControl. This provides a solid foundation for token… |
| **Governance / Economics** | 2/10 | High | The economic model of the NEXST token is significantly influenced by centralized governance. The ability for a privileged role to `mint` new tokens (7.4 Economic) allows for arbitrary supply… |
| **Upgrades** | 3/10 | High | The NEXST token contract is not designed as an upgradeable proxy (7.7 Upgrades), meaning its logic cannot be modified after deployment. This eliminates upgrade-related risks such as proxy… |

## Security Findings

_🟠 1 High · 🟡 3 Medium · ⚪ 3 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 0.0% in wallets, 100.0% in other contracts. The deployer/owner wallet itself holds 24.2%. A holder that also controls the contract can sell into its own liquidity. 1 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `CP-01` — Centralized Minting Capability  *(Severity: Medium · Status: Unresolved)*

A specific role has the power to create new NEXST tokens at any time by calling the `mint(address,uint256)` function. This means the total supply of NEXST tokens can be increased arbitrarily, which could dilute the value of existing tokens held by others.

**Recommendation:** Token holders should be aware that the supply of NEXST tokens is not fixed and can be increased by the designated `MINTER_ROLE`. The project team should clearly communicate the policies and circumstances under which new tokens will be minted.


### `CP-04` — Centralized Transfer Pause  *(Severity: Medium · Status: Unresolved)*

The contract owner has the ability to temporarily stop all NEXST token transfers by calling the `pause()` function. They can also resume transfers using `unpause()`. This means the owner can prevent token holders from moving or selling their tokens at any time, potentially impacting liquidity and market access.

**Recommendation:** Token holders should understand that their ability to transfer NEXST tokens can be halted by the contract owner. The project team should establish and communicate clear policies for when and why the pause functionality would be used, and ideally, implement a timelock for such critical actions.


### `CP-06` — Centralized Blacklisting Capability  *(Severity: Medium · Status: Unresolved)*

The contract owner can prevent specific addresses from transferring or receiving NEXST tokens by adding them to a blacklist using the `setBlacklist(address,bool)` function. This allows the owner to freeze funds or restrict access for individual token holders without their consent.

**Recommendation:** Token holders should be aware that their address can be blacklisted by the contract owner, preventing them from interacting with their NEXST tokens. The project team should provide transparent guidelines on the criteria for blacklisting and consider mechanisms for dispute resolution.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as NEXST (NXT), market cap $13M, rank #1082. 1 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $814K (DexScreener, all pools). 24h trading volume $2.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-5 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $814K of DEX liquidity across 1 pools. Launch: 157 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xae74...16c1`](https://bscscan.com/address/0xae7484d162ba80b340eba7769a7a67838b1c16c1) |
| **Network** | BNB Chain |
| **Price** | $0.06332 |
| **24h Volume** | $1.35M |
| **Liquidity** | $813.9K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1974 buys / 1072 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xb09634eda7489531964851b57527b2ef043af563)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nexst-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-16*
