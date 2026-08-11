---
token: Vestra DAO
ticker: VSTR
network: ethereum
risk_score: 47
status: high
date: 2026-08-11
---

# Vestra DAO (VSTR) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 47/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vestra-dao-eth)

---

## Audit Summary

The VestraDAO token contract is an ERC20 token with added burnable and permit functionalities, incorporating a blacklist mechanism that relies on an external DAO contract. The contract utilizes well-audited OpenZeppelin libraries, contributing to its foundational security. However, the core blacklist functionality introduces significant centralization and immutability risks, especially given that ownership has been renounced. The reliance on an external, immutable DAO address for blacklisting, coupled with the potential for operational failure if not configured correctly, elevates the overall risk profile to High.

> **Final Recommendation:** Given the high centralization and immutability of the blacklist mechanism, it is crucial to ensure the `dao` address points to an extremely robust and secure `IDAO` contract. Thoroughly audit the `IDAO` contract and its governance model to mitigate the risk of arbitrary blacklisting or compromise. Consider implementing a multi-signature wallet for the `IDAO` contract's control to distribute authority. For future iterations, evaluate the trade-offs of immutability versus the need for emergency response or adaptability, potentially exploring upgradeable contract patterns with robust governance for critical components.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The VestraDAO contract is built upon robust OpenZeppelin ERC20, ERC20Burnable, Ownable, and ERC20Permit implementations, ensuring a solid foundation for standard token operations (7.2 Code Security).… |
| **Governance / Economics** | 1/10 | High | The economic model centers around an ERC20 token with a blacklist feature. A significant economic risk (7.4 Economic) stems from the initial minting of 50 billion tokens to the `initialOwner`… |
| **Upgrades** | 8/10 | Low | The VestraDAO contract is not designed with an upgrade mechanism (7.7 Upgrades). It is a standard, non-proxy contract, meaning its logic is immutable once deployed. This eliminates risks associated… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Immutable and Critical External Dependency for Blacklist  *(Severity: High · Status: Unresolved)*

The `VestraDAO` contract relies on an external `IDAO` contract, specified by the `dao` address, for its core blacklist functionality. The `setDaoAddress` function, which sets this critical dependency, is `onlyOwner`. Given that ownership has been renounced, the `dao` address is now immutable. This means if the external `IDAO` contract at the specified address is compromised, becomes malicious, or requires an update (e.g., due to a vulnerability or change in project governance), the `VestraDAO` token cannot update its dependency. This could lead to permanent fund locks for legitimate users, arbitrary blacklisting, or a complete breakdown of token functionality without any recourse.

**Recommendation:** Ensure the `IDAO` contract at the set `dao` address is exceptionally secure, thoroughly audited, and has a robust, decentralized governance model. Since the address is immutable, any future issues with the `IDAO` contract cannot be mitigated by the `VestraDAO` token. Consider a design where the blacklist authority is more resilient or can be updated through a community-governed process, even if the token contract itself is immutable.


### `M-01` — Blacklist Mechanism Operational Risk Post-Renunciation  *(Severity: Medium · Status: Unresolved)*

The `dao` address, which is critical for the blacklist functionality, is initialized to `address(0)` and can only be set once by the `owner` via `setDaoAddress`. If the `owner` renounced ownership *before* calling `setDaoAddress` with a valid `IDAO` contract address, the `dao` variable would remain `address(0)`. Subsequent calls to `isBlackList` would attempt to interact with `IDAO(address(0))`, which will always revert. This would render all core token functions (`transfer`, `approve`, `transferFrom`, `burn`, `burnFrom`) unusable, effectively locking all tokens and making the contract inoperable.

**Recommendation:** Verify that the `dao` address was correctly set to a valid and functional `IDAO` contract address immediately after deployment and *before* ownership was renounced. For future deployments, ensure a strict deployment checklist is followed to prevent such operational failures. If the contract is already deployed and `dao` is `address(0)` with ownership renounced, the contract is effectively broken.


### `L-01` — Lack of Emergency Pause Mechanism  *(Severity: Low · Status: Unresolved)*

The contract lacks a general pause mechanism (e.g., `Pausable` from OpenZeppelin) that could temporarily halt token transfers, approvals, or burns in the event of a critical vulnerability in an integrated DeFi protocol or a widespread exploit. While the blacklist can restrict individual accounts, it cannot provide a global emergency stop. This limits the ability to react swiftly to unforeseen, systemic risks affecting the token or its ecosystem.

**Recommendation:** Consider implementing a pause functionality, ideally controlled by a multi-signature wallet or a decentralized governance mechanism. This would allow for a rapid response to critical situations, protecting user funds and the protocol's integrity. However, given the contract's immutability, this would require a redeployment.


### `I-01` — Initial Token Distribution Centralization  *(Severity: Informational · Status: Unresolved)*

The constructor mints the entire initial supply of 50,000,000,000 tokens (adjusted for decimals) directly to the `initialOwner`. This results in a highly centralized initial distribution, granting significant control and influence over the token's ecosystem to a single address. While not a direct vulnerability, this centralization can pose governance and market manipulation risks.

**Recommendation:** For future token designs, consider a more distributed initial token allocation strategy, potentially involving vesting schedules, community airdrops, or multi-signature controlled treasuries to mitigate centralization risks and foster broader participation.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x92d5...b434`](https://etherscan.io/address/0x92d5942f468447f1f21c2092580f15544923b434) |
| **Network** | Ethereum |
| **Price** | $0.00524 |
| **24h Volume** | $71.1K |
| **Liquidity** | $986.1K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 98.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 65 buys / 38 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x2349a69875aad7beb787f6f230ea2d71a52d6283)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vestra-dao-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
