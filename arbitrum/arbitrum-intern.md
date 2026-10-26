---
token: Arbitrum Intern
ticker: INTERN
network: arbitrum
risk_score: 43
status: medium
date: 2026-08-31
---

# Arbitrum Intern (INTERN) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/arbitrum-intern-arb)

---

## Audit Summary

The OdysToken contract implements an ERC-20-like token with initial anti-whale and anti-bot transfer restrictions. The contract utilizes an immutable 'factory' address for initial configuration. While the core ERC-20 functionality is standard, the custom transfer logic and extensive exemption list introduce specific risks related to centralization and potential circumvention of restrictions. The contract is not upgradeable, which eliminates upgrade-related risks.

> **Final Recommendation:** It is recommended to carefully manage the private key associated with the `factory` address due to its significant control over initial token parameters and exemptions. Consider implementing a multi-signature wallet for the `factory` address to enhance security and decentralize control. Review the `maxTx` calculation logic to ensure it aligns with the intended anti-whale mechanism, potentially capping `maxTx` at `maxWallet` or a smaller percentage. For better off-chain monitoring, emit events when critical parameters like `liquidityPool` or `initialBuyRecipient` are set.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The OdysToken contract provides standard ERC-20 functionality with added transfer restrictions during an initial 'guarded' period (7.2 Code Security). The `factory` address, set at deployment, has… |
| **Governance / Economics** | 1/10 | High | The token's economic model includes temporary anti-whale and anti-bot measures via `maxWalletBps` and `restrictionSeconds` (7.4 Economic). The `maxTx` calculation allows transactions up to 110% of… |
| **Upgrades** | 6/10 | Medium | The OdysToken contract is not designed as an upgradeable proxy (7.7 Upgrades). It is a standard implementation contract, meaning its logic cannot be changed after deployment. This eliminates any… |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Extensive Exemption List from Transfer Restrictions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_exempt` function includes a broad list of addresses (`factory`, `positionManager`, `swapRouter`, `liquidityPool`, `address(this)`, `address(0)`, `DEAD`, `initialBuyRecipient`) that are not subject to the `maxWallet` or `maxTx` transfer restrictions. While some exemptions are necessary (e.g., `address(0)`, `DEAD`), others like `positionManager`, `swapRouter`, `liquidityPool`, and `initialBuyRecipient` represent external contracts or designated recipients. If any of these external contracts are compromised or behave unexpectedly, they could be used to bypass the intended anti-whale/anti-bot mechanisms, potentially

**Recommendation:** Carefully review each address in the `_exempt` list. Ensure that the trust placed in these external contracts/addresses is justified and that their security posture is robust. Consider if all these addresses truly require full exemption from transfer limits, or if some could operate within certain bounds.


### `M-02` — `maxTx` Calculation Allows Transfers Exceeding `maxWallet`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `maxTx()` function calculates the maximum allowed transaction size as `110%` of `maxWallet()`. This design choice means that a single transfer can be larger than the maximum amount a wallet is permitted to hold. While this might be intended for flexibility, it could potentially allow sophisticated users to circumvent the `maxWallet` restriction by repeatedly buying `maxTx` amounts and distributing them across multiple controlled wallets, effectively accumulating more than the `maxWallet` limit across their holdings.

**Recommendation:** Re-evaluate the `maxTx` calculation. If the goal is to prevent large accumulations, consider capping `maxTx` at `maxWallet` or a smaller percentage to prevent easy circumvention of the anti-whale mechanism. Ensure the intended behavior aligns with the current implementation.


### `M-03` — Centralization Risk with `factory` Address  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `factory` address, set to `msg.sender` during deployment, possesses significant administrative control. It is the only address authorized to call `setPool` and `setInitialBuyRecipient`, which configure critical parameters like the `liquidityPool` and `initialBuyRecipient`. Furthermore, the `factory` address is explicitly exempt from all transfer restrictions (`maxWallet` and `maxTx`). A compromise of this single address could lead to unauthorized manipulation of the token's initial setup or unrestricted movement of tokens, potentially undermining the token's economic stability or initial distribution.

**Recommendation:** Consider implementing a multi-signature wallet for the `factory` address to distribute control and reduce the risk of a single point of failure. If a multi-sig is not feasible, ensure the private key for the `factory` address is secured with the highest possible standards.


### `L-01` — Lack of Events for Critical State Changes  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `setPool` and `setInitialBuyRecipient` functions modify critical state variables (`liquidityPool` and `initialBuyRecipient`) but do not emit corresponding events. Without events, off-chain monitoring tools and users cannot easily track changes to these important addresses, making it harder to detect unauthorized or unexpected modifications.

**Recommendation:** Emit events after successfully updating `liquidityPool` and `initialBuyRecipient`. For example, `event PoolSet(address indexed oldPool, address indexed newPool);` and `event InitialBuyRecipientSet(address indexed oldRecipient, address indexed newRecipient);`.


### `I-01` — `maxWalletBps == 0` Disables All Restrictions  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). If the `maxWalletBps` parameter is initialized to `0` in the constructor, both `maxWallet()` and `maxTx()` functions will return `type(uint256).max`. This effectively disables all anti-whale and anti-bot transfer restrictions for the entire duration of the `restrictionSeconds` period. While this might be an intentional configuration option to launch without restrictions, it's important to be aware that the core restriction logic can be entirely bypassed by this single parameter.

**Recommendation:** Ensure that the implications of setting `maxWalletBps` to `0` are fully understood and align with the project's launch strategy. If restrictions are intended, ensure `maxWalletBps` is set to a non-zero value.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2360...b3c8`](https://arbiscan.io/address/0x23607980905fad2199538509a1a262a31e36b3c8) |
| **Network** | Arbitrum |
| **Price** | $0.00001696 |
| **24h Volume** | $1.9K |
| **Liquidity** | $14.1K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 15h |
| **Top-10 Holders** | 79.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 445 buys / 249 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0xd2aa4d742c7990d7a74c767028f663e25692fef0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/arbitrum-intern-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
