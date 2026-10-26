---
token: Coinbase Wrapped Staked ETH
ticker: CBETH
network: base
risk_score: 11
status: low
date: 2026-08-11
---

# Coinbase Wrapped Staked ETH (CBETH) — Smart Contract Security Analysis | Base

> **Risk Score: 11/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-staked-eth-base)

---

## Audit Summary

This audit covers an upgradeable ERC20 token, `UpgradeableOptimismMintableERC20`, deployed on the Base network via an EIP-1967 Transparent Proxy. The contract utilizes OpenZeppelin's `Initializable` and `ERC20Upgradeable` patterns, providing a solid foundation. Key risks identified include the centralized control over token supply through a minting function and the inherent complexities associated with upgradeable contracts, despite being managed by a multisig.

> **Final Recommendation:** It is recommended to ensure the multisig signers are well-known, trusted entities with robust key management practices. A clear, documented process for upgrade proposals and execution, including thorough testing on a staging environment, should be established. For critical administrative actions, especially minting or upgrades, consider implementing a timelock to provide a window for community review and reaction, enhancing transparency and security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract leverages OpenZeppelin's battle-tested `ERC20Upgradeable` and `Initializable` patterns, providing a robust and secure foundation (7.1 Architecture, 7.2 Code Security). Solidity 0.8.15… |
| **Governance / Economics** | 9/10 | Low | The prefill indicates the presence of a minting function, which implies a centralized authority can control the token supply (7.4 Economic). This introduces a significant economic risk due to… |
| **Upgrades** | 7/10 | Low | The contract is deployed behind an EIP-1967 Transparent Proxy, managed by a 3/6 multisig (7.7 Upgrades). This setup allows for secure future upgrades, reducing single points of failure for… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | Multisig — 3-of-6 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 32.3% |
| **Top-3 Unlocked** | 61.5% |

## Security Findings

_🟡 1 Medium · ⚪ 8 Informational_

### `M-02` — Potential for Reentrancy in Derived Contracts via `_beforeTokenTransfer` Hook  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_transfer` function in `ERC20Upgradeable` includes a call to `_beforeTokenTransfer`, which is an internal virtual function. While the base OpenZeppelin implementation is safe, if the `UpgradeableOptimismMintableERC20` contract (or any future derived contract) overrides this hook with external calls or state-changing logic before updating balances, it could introduce reentrancy vulnerabilities. This is a common pattern for custom logic but requires careful implementation to avoid security pitfalls.

**Recommendation:** When overriding `_beforeTokenTransfer` in `UpgradeableOptimismMintableERC20` or any derived contract, ensure that no external calls are made before all state changes related to the transfer are finalized. Follow the Checks-Effects-Interactions pattern strictly. If external calls are necessary, implement reentrancy guards.


### `I-01` — Dependency on External Multisig Security  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The overall security of the system, particularly regarding upgrades and administrative actions, is highly dependent on the security practices and trustworthiness of the 3/6 multisig signers controlling the proxy admin. Compromise of the required number of keys (3 out of 6) could lead to unauthorized control over the contract, including malicious upgrades or administrative actions.

**Recommendation:** Ensure that the multisig signers are diverse, geographically distributed, and employ strong key management practices (e.g., hardware wallets, secure offline storage). Regularly review and update multisig signers as personnel or security requirements change. Consider implementing a robust incident response plan for potential multisig key compromises.


### `I-02` — Centralized Control over Token Supply (Minting)  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `UpgradeableOptimismMintableERC20` contract, as indicated by `has_mint: true` in the prefill, includes a minting function. This grants a privileged role (likely an owner or minter) the ability to create new tokens, introducing a significant economic risk due to potential arbitrary inflation of the token supply. This centralizes control over the token's economic model, which could devalue existing tokens if misused.

**Recommendation:** Clearly document the role responsible for minting, the conditions under which minting can occur, and any governance processes required. Consider implementing a timelock for minting operations to provide transparency and allow for community oversight. If possible, explore mechanisms to decentralize or restrict minting capabilities over time.


### `I-03` — Upgradeability via Multisig Admin  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is upgradeable via an EIP-1967 Transparent Proxy, with administration controlled by a 3/6 multisig. While the multisig provides a layer of security by requiring multiple approvals, any upgrade introduces inherent risks such as potential for logic errors, storage collisions, or malicious changes if the multisig signers are compromised or collude. Upgrades always carry a non-zero risk of introducing new vulnerabilities.

**Recommendation:** Implement a robust upgrade process including comprehensive testing on a staging environment before deployment to production. Conduct independent audits of all proposed upgrade logic. Consider adding a timelock to the proxy admin to allow for a delay between an upgrade proposal and its execution, providing a window for review and potential intervention.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 91.7% of supply. What remains: 0.7% in wallets, 90.9% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Coinbase Wrapped Staked ETH (CBETH), market cap $459M. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $7.5M (DexScreener, all pools). 24h trading volume $5.2M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner key — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Liquid staking token  *(Severity: Informational · Status: Acknowledged)*

A receipt for staked native tokens that keeps earning staking rewards. Its value depends on the staking protocol and its validators. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Liquid Staking Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner key. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $7.5M of DEX liquidity across 30 pools. Launch: 375 days of market history.

**Recommendation:** Check the staking protocol's validator set, withdrawal queue and governance.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2ae3...ec22`](https://basescan.org/address/0x2ae3f1ec7f1f5012cfeab0185bfc7aa3cf0dec22) |
| **Network** | Base |
| **Price** | $2,857.7000 |
| **24h Volume** | $5.24M |
| **Liquidity** | $2.82M |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 91.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 411 buys / 359 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xb1383dc47d9971fc999c3a9088f79e744b376e97)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-staked-eth-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
