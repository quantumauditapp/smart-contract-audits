---
token: Moltbook
ticker: MOLT
network: base
risk_score: 30
status: medium
date: 2026-07-24
---

# Moltbook (MOLT) — Smart Contract Security Analysis | Base

> **Risk Score: 30/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/moltbook-base)

---

## Audit Summary

The ClankerToken contract is an ERC20 token implementation with extensions for burning, permit functionality, and voting, alongside custom cross-chain mint/burn capabilities and administrative controls for metadata. The contract leverages well-audited OpenZeppelin libraries. Key findings include centralized administrative control over critical parameters and a reliance on an external bridge for supply management, which are common patterns but introduce specific risks.

> **Final Recommendation:** To enhance the security posture of the ClankerToken, it is recommended to implement a multi-signature wallet for the `_admin` role to mitigate the risk of a single point of failure. Additionally, ensure robust monitoring and operational procedures are in place for the `SUPERCHAIN_TOKEN_BRIDGE` given its critical role in token supply management. Consider documenting the purpose and secure management of the `_originalAdmin` key and the `verify()` function.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract demonstrates a solid technical foundation, inheriting from battle-tested OpenZeppelin ERC20 and its extensions (ERC20Permit, ERC20Votes, ERC20Burnable). The implementation of `_update`… |
| **Governance / Economics** | 5/10 | Medium | The token incorporates `ERC20Votes`, indicating an intention for governance participation (7.5 Governance). The initial supply is minted on a specific chain, and cross-chain supply adjustments are… |
| **Upgrades** | 9/10 | Low | The ClankerToken contract is not designed as an upgradeable proxy (7.7 Upgrades). It is a standard implementation contract. Therefore, there are no specific upgrade-related risks inherent in its… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Centralized Admin Control Over Critical Functions  *(Severity: High · Status: Unresolved)*

The `_admin` address has the sole authority to call `updateAdmin()`, `updateImage()`, and `updateMetadata()`. This means a single compromised private key for the `_admin` could lead to the transfer of administrative control to an attacker, or arbitrary changes to the token's image and metadata, potentially impacting its public perception and integration with external platforms. This is a significant centralization risk (7.3 Access Control, 7.8 Operations).

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the `_admin` role to require multiple approvals for sensitive operations. Alternatively, consider a time-locked governance mechanism for critical changes to allow community oversight and reaction time.


### `M-01` — Reliance on External Superchain Token Bridge for Supply Control  *(Severity: Medium · Status: Unresolved)*

The `crosschainMint()` and `crosschainBurn()` functions, which directly affect the token's supply, are exclusively callable by `Predeploys.SUPERCHAIN_TOKEN_BRIDGE`. The security and integrity of the token's total supply across chains are entirely dependent on the correct functioning and security of this external bridge contract. Any vulnerability or compromise in the `SUPERCHAIN_TOKEN_BRIDGE` could lead to unauthorized minting or burning of ClankerTokens (7.4 Economic, 7.6 External).

**Recommendation:** Ensure the `SUPERCHAIN_TOKEN_BRIDGE` contract is rigorously audited, continuously monitored, and has robust security measures in place. Transparently communicate this dependency and its implications to token holders. While this is a common pattern for L2 canonical tokens, it's crucial to acknowledge and manage the associated external risk.


### `L-01` — Immutability of `_originalAdmin` and One-Time `verify()` Call  *(Severity: Low · Status: Unresolved)*

The `_originalAdmin` address is immutable and is the only address capable of calling the `verify()` function, which sets the `_verified` boolean to true. If the private key for `_originalAdmin` is lost or becomes inaccessible before `verify()` is called, this function can never be executed. While the impact of `_verified` is not immediately clear from the contract, this represents a minor operational inflexibility (7.8 Operations).

**Recommendation:** Ensure the `_originalAdmin` key is securely managed and backed up. Clearly document the purpose and importance of the `verify()` function and the `_originalAdmin` role within the protocol's overall design.


### `L-02` — Lack of Emergency Pause Mechanism  *(Severity: Low · Status: Unresolved)*

The contract does not include a mechanism to pause token transfers or other critical operations in an emergency. In the event of a critical vulnerability discovery (e.g., in an external dependency or the token itself), the protocol would lack the ability to temporarily halt operations to prevent further damage or exploit (7.8 Operations).

**Recommendation:** Consider integrating a pausable mechanism (e.g., OpenZeppelin's `Pausable` contract) controlled by the `_admin` (preferably a multisig) to allow for emergency halts of token transfers. This adds a layer of protection against unforeseen circumstances.


### `I-01` — Centralized Control Over Token Metadata  *(Severity: Informational · Status: Unresolved)*

The `_admin` address has the ability to unilaterally update the token's `_image` and `_metadata` strings via `updateImage()` and `updateMetadata()`. While this provides flexibility for branding and information updates, it means the token's public representation can be changed by a single entity without broader community consensus. This is a design choice that centralizes control over external perception (7.4 Economic, 7.5 Governance).

**Recommendation:** Clearly communicate the centralized nature of metadata updates to the community. If decentralization is a long-term goal, consider transitioning metadata updates to a governance-controlled mechanism, perhaps with a time-lock, to ensure community input and transparency.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb695...ab07`](https://basescan.org/address/0xb695559b26bb2c9703ef1935c37aeae9526bab07) |
| **Network** | Base |
| **Price** | $0.00000324 |
| **24h Volume** | $3.5K |
| **Liquidity** | $1.03M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 47.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 301 buys / 639 sells |

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

## Frequently Asked Questions

### Is Moltbook a scam?

Based on automated analysis, Moltbook scores 20/100 (Low Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Moltbook safe to buy?

Our scanner flagged a risk score of 20/100. Ownership is renounced which reduces rug-pull risk. DYOR before purchasing any token.

### Has Moltbook been audited?

The contract is open-source and verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x15f351bf1637b43d70631ba95fb9bbb1ff21761c29b034c1b380aecb922464dd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/moltbook-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-24*
