---
token: PRDCTR
ticker: PRD
network: ethereum
risk_score: 47
status: high
date: 2026-08-17
---

# PRDCTR (PRD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 47/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/prdctr-eth)

---

## Audit Summary

The audit of the ConfigurableTokenUpgradeable contract, deployed via an ERC1967Proxy, reveals a well-structured and minimal ERC-20 token implementation. The contract leverages battle-tested OpenZeppelin upgradeable libraries for ERC-20, ERC-20 Permit, Ownable, and UUPS functionality. No critical or high-severity vulnerabilities were identified. Minor observations include the custom decimals implementation and the reinitializer for ERC20Permit. Centralized control by the owner (a multisig) for upgrades and initial configuration is noted, which is typical for such tokens.

> **Final Recommendation:** It is recommended to maintain robust operational security practices for the multisig wallet controlling the contract owner address, given its extensive control over upgrades and token configuration. Regular reviews of multisig signers and their security postures are crucial. For enhanced decentralization and safety, consider implementing a time-lock mechanism for critical owner-controlled operations, especially contract upgrades, to provide a window for community review and reaction.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1) is robust, utilizing OpenZeppelin's upgradeable contracts for ERC-20, ERC-20 Permit, Ownable, and UUPS proxy patterns. Code security (7.2) is high, benefiting from… |
| **Governance / Economics** | 4/10 | Medium | The economic model (7.4) is that of a standard ERC-20 token with an initial supply minted to a specified holder. Governance (7.5) is centralized, with the contract owner having control over initial… |
| **Upgrades** | 1/10 | High | The contract implements the UUPS upgrade pattern (7.7), with the `_authorizeUpgrade` function correctly restricted to the `onlyOwner` modifier. This ensures that only the designated owner can… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | ⚠️ 1 |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 36.5% — UNCX Locker |
| **Top-1 Unlocked Holder** | ⚠️ 63.5% |
| **Top-3 Unlocked** | 63.5% |

## Security Findings

_🟢 1 Low · ⚪ 2 Informational_

### `L-01` — Centralized Control by Owner  *(Severity: Low · Status: Unresolved)*

The `ConfigurableTokenUpgradeable` contract grants significant control to the contract owner, including the ability to authorize contract upgrades (`_authorizeUpgrade`), transfer ownership, and renounce ownership. The initial token configuration (name, symbol, decimals, initial supply, initial holder) is also set by the owner during initialization. The prefill indicates the owner is a 2/4 multisig.

**Recommendation:** While the use of a multisig wallet for ownership significantly mitigates the risk of a single point of failure, it is crucial that the multisig signers are trustworthy, follow robust operational security practices, and that the multisig threshold is appropriate for the protocol's risk profile. Consider implementing time-locks for critical operations like upgrades if further decentralization or safety is desired.


### `I-01` — Custom Decimals Implementation  *(Severity: Informational · Status: Unresolved)*

The `ConfigurableTokenUpgradeable` contract overrides the `decimals()` function from `ERC20Upgradeable` to return a custom `_decimals` value set during initialization, rather than the default 18. While this provides flexibility, it deviates from the common ERC-20 standard of 18 decimals.

**Recommendation:** Ensure all integrations and user interfaces are aware of and correctly handle the token's configurable decimal count to prevent display issues or misinterpretations. Clearly document this design choice in external documentation.


### `I-02` — Reinitializer for ERC20Permit  *(Severity: Informational · Status: Unresolved)*

The `initializePermit()` function is marked as a `reinitializer(2)`, allowing it to be called multiple times if the reinitialization flag for slot 2 is reset. This function re-initializes the `ERC20Permit` component by calling `__ERC20Permit_init(name())`.

**Recommendation:** Confirm the specific use case and necessity for `ERC20Permit` re-initialization. While generally safe, ensure that repeated calls do not introduce unexpected state changes or gas inefficiencies if not genuinely required.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc847...efe5`](https://etherscan.io/address/0xc84782858b7bef5d25182dbac956a6aa463aefe5) |
| **Network** | Ethereum |
| **Price** | $0.0006856 |
| **24h Volume** | $107.4K |
| **Liquidity** | $5.11M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 96.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 67 buys / 66 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x45aecbbcc9b5414bcfd84f1ae5f3d9f5488ba403)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/prdctr-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-17*
