---
token: BORT
ticker: BORT
network: bsc
risk_score: 0
status: low
date: 2026-09-04
---

# BORT (BORT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bort-bsc)

---

## Audit Summary

The FourERC20 contract is a standard ERC-20 token implementation, largely based on OpenZeppelin Contracts. It provides core token functionalities like transfer, allowance, minting, and burning. The contract demonstrates high code quality and adherence to established standards, leveraging battle-tested libraries. Key design considerations include the internal nature of supply management and initialization functions, which require a derived contract for external exposure and access control. Potential risks are primarily informational or low-severity, related to design patterns and standard ERC-20 behaviors.

> **Final Recommendation:** For any derived contract built upon FourERC20, ensure that external functions for `_mint`, `_burn`, and `_init` are implemented with robust access control, ideally using a multi-signature wallet or a time-locked governance mechanism to mitigate centralization risks. Educate users on the safer `increaseAllowance` and `decreaseAllowance` functions to avoid potential front-running issues associated with the standard `approve` function. Consider emitting events for critical state changes, such as token initialization, to enhance transparency and off-chain monitoring capabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1) of the FourERC20 contract is robust, being a direct implementation of the ERC-20 standard using OpenZeppelin's battle-tested libraries, which significantly reduces… |
| **Governance / Economics** | 10/10 | Low | The economic model (7.4) of the FourERC20 token is a standard ERC-20, with its supply mechanism left to a derived contract. If a derived contract implements minting/burning, there is a potential for… |
| **Upgrades** | 10/10 | Low | The FourERC20 contract is not designed as an upgradeable proxy (7.7). It is intended to be deployed as a standalone, immutable contract or as an implementation contract for a proxy pattern managed… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟢 2 Low · ⚪ 2 Informational_

### `L-01` — Centralized Control over Token Supply (if implemented in derived contract)  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). If a derived contract exposes `_mint` and `_burn` functions, they would typically be controlled by an owner or a multi-sig. This introduces a point of centralization (7.3, 7.4) where a single entity (or a small group) can control the token supply, potentially leading to inflation or deflation without broader community consensus. This is a common design pattern for many tokens but represents a centralization risk.

**Recommendation:** For derived contracts, implement robust access control for minting/burning functions, ideally with multi-sig or time-locked mechanisms, or consider a fixed supply model if dynamic supply is not required. Transparency around the minting/burning authority is crucial.


### `L-02` — Standard ERC-20 `approve` Front-Running Risk  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract includes `increaseAllowance` and `decreaseAllowance` to mitigate the known ERC-20 `approve` front-running vulnerability. However, the standard `approve` function is still present and can be vulnerable if users directly interact with it by approving a new non-zero amount without first setting the allowance to zero. An attacker could front-run the transaction, spend the original allowance, and then the new allowance would also be granted, leading to a double-spend of the intended allowance amount.

**Recommendation:** Educate users to prefer `increaseAllowance` and `decreaseAllowance` or to follow the two-step approval process (approve 0, then approve new amount) when using the `approve` function directly. This is a common best practice for ERC-20 token interactions.


### `I-01` — Base Contract Design for Supply Management and Initialization  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `FourERC20` contract provides internal functions (`_mint`, `_burn`, `_init`) for token supply management and initialization (setting name/symbol). These functions are not exposed externally by this contract. This design requires a derived contract to implement external interfaces for these functionalities, including appropriate access control, or to call `_init` in its constructor. If deployed directly without a derived contract, the token's name/symbol cannot be set, and its supply cannot be managed.

**Recommendation:** Ensure that any derived contract properly implements and secures the external interfaces for `_mint`, `_burn`, and calls `_init` in its constructor to set the token's metadata. This design choice should be clearly documented and understood by developers integrating with the token.


### `I-02` — Missing Events for `_init` Parameters  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_init` function, intended for setting the token's name and symbol, does not emit an event upon execution. While not a security vulnerability, emitting an event for initialization parameters can be useful for off-chain monitoring, indexing, and transparency regarding the token's metadata (7.8 Operations).

**Recommendation:** Consider adding an event (e.g., `event Initialized(string name, string symbol);`) and emitting it within the `_init` function. This enhances the traceability and observability of the token's initial configuration.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2a84...4444`](https://bscscan.com/address/0x2a846aaaf896ef393ccb76398c1d96ea97374444) |
| **Network** | BNB Chain |
| **Price** | $0.001066 |
| **24h Volume** | $102.9K |
| **Liquidity** | $192.3K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 39.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 257 buys / 342 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x76c42dda1de814ac60951c2c89c77dbecfb86ffb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bort-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-04*
