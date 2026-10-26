---
token: NEAR Protocol
ticker: NEAR
network: bsc
risk_score: 12
status: low
date: 2026-09-28
---

# NEAR Protocol (NEAR) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/near-protocol-bsc)

---

## Audit Summary

The BEP20 Token implementation contract exhibits a high overall risk level primarily due to centralized minting capabilities controlled by the owner and a critical code integrity issue with a truncated internal function. While the contract correctly implements the upgradeable proxy pattern and uses SafeMath for arithmetic operations, the owner's ability to mint tokens poses a significant economic risk. Additionally, the `_burnFrom` function is incomplete, indicating a potential flaw in the deployed code's completeness or quality. The owner also has the ability to irreversibly renounce ownership, which could lead to a loss of administrative control.

> **Final Recommendation:** It is strongly recommended to address the truncated `_burnFrom` function by completing or removing it to ensure code integrity and prevent potential runtime errors if the function is ever invoked. The centralized minting capability should be carefully considered; if not essential, it should be removed or placed under a more decentralized governance mechanism. Furthermore, the `renounceOwnership` function should be used with extreme caution, as its execution leads to an irreversible loss of administrative control. Consider implementing a multi-signature wallet for ownership to enhance security and prevent single points of failure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract utilizes SafeMath for robust arithmetic operations, mitigating common integer overflow/underflow vulnerabilities. However, a significant technical flaw exists with the truncated… |
| **Governance / Economics** | 9/10 | Low | The contract's economic model presents a high risk due to the centralized minting capability (H-02), allowing the owner to arbitrarily increase token supply and dilute value. While the `_mintable`… |
| **Upgrades** | 2/10 | High | The contract correctly implements the `Initializable` pattern and features an empty constructor (I-01), adhering to best practices for upgradeable proxy implementations. This design minimizes the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 66.5% |
| **Top-3 Unlocked** | 74.0% |

## Security Findings

_🟡 1 Medium · ⚪ 9 Informational_

### `M-02` — Truncated `_burnFrom` Function  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_burnFrom` internal function is incomplete in the provided source code, ending abruptly. While this function is not currently called by any other function within the contract, its truncation represents a significant code integrity flaw. If a future function or an upgrade were to rely on `_burnFrom`, it would lead to runtime errors or unexpected behavior. This indicates a potential issue with the deployed code's completeness or quality.

**Recommendation:** Review the original source code for the `_burnFrom` function. If it is intended to be part of the contract, ensure its full and correct implementation. If it is not intended for use, consider removing the incomplete function to avoid confusion and potential future issues.


### `I-01` — Standard Proxy Implementation Pattern  *(Severity: Informational · Status: Resolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract correctly implements the `Initializable` pattern and has an empty `constructor`, which is standard practice for upgradeable contracts designed to be used as an implementation behind a proxy. This ensures proper initialization through the `initialize` function and avoids issues with proxy storage collisions.

**Recommendation:** No specific recommendation. This is a best practice for upgradeable contracts.


### `I-02` — Centralized Minting Capability  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `mint` function allows the contract owner to create an arbitrary amount of new tokens, provided the `_mintable` flag is set to `true` during initialization. This centralized control over token supply introduces significant economic risk, as the owner can dilute the value of existing tokens at will, potentially harming token holders.

**Recommendation:** Evaluate if centralized minting is a necessary feature for the token's economic model. If not, consider removing the `mint` function and setting `_mintable` to `false` permanently. If minting is required, implement a more decentralized or time-locked mechanism, such as a governance-controlled minting schedule or a multi-signature approval process, to reduce the risk of arbitrary supply inflation.


### `I-03` — Irreversible Renouncement of Ownership  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `renounceOwnership` function allows the current owner to transfer ownership to the zero address (`address(0)`). If executed, this action is irreversible and would leave the contract without an owner. Consequently, all `onlyOwner` functions, including `mint` (if `_mintable` is true) and `transferOwnership`, would become permanently inaccessible, potentially hindering future administrative actions or upgrades.

**Recommendation:** Owners should exercise extreme caution when using `renounceOwnership`. It is recommended to transfer ownership to a secure, multi-signature wallet or a robust governance contract instead of renouncing it to the zero address, unless the intention is to permanently decentralize control over all owner-restricted functions.


### `I-04` — Immutability of `_mintable` Flag  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_mintable` flag, which controls whether new tokens can be minted, is set only during the `initialize` function and cannot be modified thereafter. This design choice means that the minting capability is permanently enabled or disabled based on the initial deployment configuration. While a clear design, it lacks flexibility for future adjustments to the token's economic policy.

**Recommendation:** If future flexibility is desired, consider implementing a function (restricted to the owner or governance) to toggle the `_mintable` flag. This would allow for dynamic adjustments to the token's minting policy without requiring a full contract upgrade.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 40.9% of supply. What remains: 35.4% in wallets, 5.5% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Binance-Peg NEAR Protocol (NEAR), market cap $59M. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $711K (DexScreener, all pools). 24h trading volume $363K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Binance-Peg Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $711K of DEX liquidity across 26 pools. Launch: 1271 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1fa4...5d63`](https://bscscan.com/address/0x1fa4a73a3f0133f0025378af00236f3abdee5d63) |
| **Network** | BNB Chain |
| **Price** | $5.1100 |
| **24h Volume** | $362.7K |
| **Liquidity** | $198.4K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 3y |
| **Top-10 Holders** | 40.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1887 buys / 1846 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x0246913ec96765bca457b0a3608872bba37d1d15)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/near-protocol-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-28*
