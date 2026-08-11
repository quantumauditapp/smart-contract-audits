---
token: Lorenzo Governance Token
ticker: BANK
network: bsc
risk_score: 65
status: high
date: 2026-08-11
---

# Lorenzo Governance Token (BANK) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lorenzo-governance-token-bsc)

---

## Audit Summary

The BankToken contract is an ERC20-compliant token with a fixed maximum supply, inheriting from OpenZeppelin's battle-tested ERC20 and ERC20Capped implementations. The primary security consideration is the centralized minting authority, `tgeContract`, which holds exclusive power to mint new tokens up to the defined cap. While the contract's technical implementation is robust, the security of the `tgeContract` is paramount to the overall integrity of the token supply.

> **Final Recommendation:** Prioritize the robust security of the `tgeContract` as it is the sole entity capable of minting new tokens. Implement multi-signature wallets, time-locks, or other robust access control mechanisms for the `tgeContract` to minimize the risk of compromise. Conduct thorough testing of the `tgeContract`'s interaction with the BankToken contract to ensure expected behavior and prevent unintended minting or supply manipulation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages OpenZeppelin's robust ERC20 and ERC20Capped implementations, ensuring adherence to established standards and mitigating common vulnerabilities (7.2 Code Security). Solidity… |
| **Governance / Economics** | 1/10 | High | The token design includes a fixed `MAX_SUPPLY` of 2.1 billion tokens, enforced by the `ERC20Capped` base contract (7.4 Economic). The `tgeContract` holds exclusive power to mint tokens up to this… |
| **Upgrades** | 6/10 | Medium | The BankToken contract is not designed to be upgradeable (7.7 Upgrades). This eliminates risks associated with proxy patterns, upgradeability logic, and potential upgrade path vulnerabilities. The… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.5% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 2 Informational_

### `H-01` — Centralized Minting Authority  *(Severity: High · Status: Unresolved)*

The `mint` function in the `BankToken` contract is restricted to `tgeContract` via `require(msg.sender == tgeContract, "Only TGE contract")`. This design centralizes the power to mint new tokens up to the `MAX_SUPPLY` in a single external address. If the `tgeContract` address is compromised, an attacker could mint the remaining supply, leading to severe token devaluation and economic instability for the protocol. While the `tgeContract` is immutable, its operational security is critical.

**Recommendation:** Implement robust security measures for the `tgeContract` address. This could include using a multi-signature wallet (e.g., Gnosis Safe), a time-lock mechanism for minting operations, or a decentralized autonomous organization (DAO) for governance over minting. Ensure the private keys controlling the `tgeContract` are stored securely and follow best practices for operational security.


### `I-01` — Use of OpenZeppelin Standards  *(Severity: Informational · Status: Resolved)*

The `BankToken` contract inherits from OpenZeppelin's `ERC20` and `ERC20Capped` contracts. These libraries are widely used, thoroughly audited, and considered industry standards for secure token implementations. This significantly reduces the risk of common vulnerabilities associated with custom token logic.

**Recommendation:** Continue to leverage battle-tested libraries for core functionalities. Regularly monitor OpenZeppelin's security advisories and updates to ensure the project benefits from ongoing security improvements.


### `I-02` — Immutability of TGE Contract Address  *(Severity: Informational · Status: Resolved)*

The `tgeContract` address, which controls the minting function, is declared as `immutable`. This ensures that the designated minting authority cannot be changed after the contract's deployment. This design choice provides certainty regarding the minting controller and prevents potential malicious reassignments.

**Recommendation:** This is a good security practice for critical addresses that should not change. Ensure the initial deployment correctly sets the intended `tgeContract` address, as it cannot be modified later.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3aee...f2bf`](https://bscscan.com/address/0x3aee7602b612de36088f3ffed8c8f10e86ebf2bf) |
| **Network** | BNB Chain |
| **Price** | $0.0375 |
| **24h Volume** | $95.3K |
| **Liquidity** | $53.8K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 93.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2025 buys / 2064 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xee6ff918a1f68b5d2fdecb14b367fa2eb5c6951c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lorenzo-governance-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
