---
token: Wrapped Coinbase Global Inc ST0x
ticker: WTCOIN
network: base
risk_score: 52
status: medium
date: 2026-09-02
---

# Wrapped Coinbase Global Inc ST0x (WTCOIN) — Smart Contract Security Analysis | Base

> **Risk Score: 52/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-coinbase-global-inc-st0x-base)

---

## Audit Summary

The StoxWrappedTokenVault contract serves as an upgradeable ERC-4626 vault implementation for a BeaconProxy. The contract leverages well-audited OpenZeppelin libraries, ensuring a solid foundation for its core vault functionalities. Key strengths include proper upgradeability patterns and basic input validation. Identified issues primarily relate to potential incompatibilities with certain ERC-20 token types and critical initialization parameter handling, leading to a Medium overall risk level.

> **Final Recommendation:** Ensure thorough due diligence on the underlying asset token to confirm its compatibility with the ERC-4626 standard, particularly regarding fee-on-transfer or rebasing mechanisms. Implement robust operational procedures for the BeaconProxy's owner, including multi-signature control and time-locks for upgrades, to mitigate centralized control risks. Verify the correctness of the initialization data, especially the asset address, during deployment to prevent critical misconfigurations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract exhibits good technical security, primarily due to its reliance on OpenZeppelin's battle-tested ERC4626Upgradeable library (7.2 Code Security). The custom logic is minimal, focusing on… |
| **Governance / Economics** | 2/10 | High | The primary economic risk (7.4 Economic) stems from the vault's potential incompatibility with non-standard ERC-20 tokens, such as fee-on-transfer or rebasing tokens, which could lead to accounting… |
| **Upgrades** | 1/10 | High | The contract is designed as an upgradeable implementation for a BeaconProxy, correctly utilizing OpenZeppelin's `Initializable` pattern (7.7 Upgrades). The `_disableInitializers()` in the constructor… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Incompatibility with Fee-on-Transfer or Rebasing Tokens  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The StoxWrappedTokenVault, as an ERC-4626 vault, does not explicitly handle fee-on-transfer or rebasing ERC-20 tokens. If the underlying `asset` token charges fees on transfers (e.g., during deposits or withdrawals) or has a rebasing mechanism, the vault's internal accounting (specifically `totalAssets()`) may not accurately reflect the actual amount of underlying tokens held. This discrepancy can lead to incorrect share prices, loss of funds for users, or denial of service for certain operations.

**Recommendation:** Before deploying with a specific asset, verify that the underlying ERC-20 token is a standard, non-rebasing, non-fee-on-transfer token. If such tokens must be supported, consider implementing custom `_deposit`, `_withdraw`, `_mint`, and `_redeem` hooks to account for token mechanics, or use a wrapper that normalizes the token's behavior.


### `L-01` — Critical Initialization Parameter (Asset Address)  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function decodes the `asset` address from `bytes calldata data`. While this pattern is common for factory-deployed clones, it makes the correct functioning of the vault entirely dependent on the accuracy of the `data` provided during the proxy's initialization. An incorrect or malicious `asset` address supplied during the initial deployment and initialization of the BeaconProxy could render the vault unusable or link it to an unintended or exploitable token.

**Recommendation:** Implement stringent checks and multi-party verification processes for the `data` parameter used during the BeaconProxy's initialization. Ensure that the `asset` address is thoroughly vetted and confirmed to be the intended token before deployment. Consider adding a mechanism to allow the Beacon owner to pause the vault or change the asset if a misconfiguration is detected, although this would add complexity.


### `I-01` — Redundant `__ERC20_init` Call  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function includes a call to `__ERC20_init("", "")`, which sets the ERC-20 name and symbol of the shares token to empty strings. However, the contract immediately overrides the `name()` and `symbol()` functions to derive these values from the underlying asset. Consequently, the `__ERC20_init` call is redundant as its effects are immediately superseded by the overrides.

**Recommendation:** The `__ERC20_init("", "")` call can be safely removed from the `initialize` function without affecting the contract's functionality or security, potentially saving a small amount of gas during initialization.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5cda...2204`](https://basescan.org/address/0x5cda0e1ca4ce2af96315f7f8963c85399c172204) |
| **Network** | Base |
| **Price** | $192.4400 |
| **24h Volume** | $557.8K |
| **Liquidity** | $39.8K |
| **Volume / Liquidity** | 14.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 86.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1044 buys / 856 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x4618dfcbc52d9fbcd45ec4a65fc61b5da57ad205)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-coinbase-global-inc-st0x-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
