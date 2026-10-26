---
token: USDS Stablecoin
ticker: USDS
network: ethereum
risk_score: 9
status: low
date: 2026-08-13
---

# USDS Stablecoin (USDS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usds-stablecoin-eth)

---

## Audit Summary

The USDS Stablecoin contract implements an ERC-20 compatible token with UUPS upgradeability and EIP-2612 permit functionality. The contract exhibits good technical practices, leveraging OpenZeppelin's battle-tested libraries. However, the audit identified a high-severity centralization risk due to the `auth` role's control over critical functions like minting and upgrades. A medium-severity finding related to unchecked arithmetic in the `mint` function was also noted, alongside low and informational findings concerning `permit` front-running and an `_isValidSignature` edge case. Addressing the centralization risk is paramount for the long-term security and trust of the protocol.

> **Final Recommendation:** To enhance the security posture of the USDS Stablecoin, it is strongly recommended to decentralize control over critical administrative functions. Implementing a robust multi-signature wallet or a decentralized autonomous organization (DAO) for the `auth` role would significantly mitigate the risks associated with a single point of failure for minting and upgrades. Additionally, review the `mint` function's `unchecked` block to either add explicit overflow checks or remove `unchecked` to rely on default Solidity 0.8+ protections, ensuring maximum safety for token supply management.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract demonstrates good technical practices, utilizing OpenZeppelin's UUPSUpgradeable for secure upgradeability and implementing EIP-2612 `permit` functionality (7.1 Architecture). Standard… |
| **Governance / Economics** | 9/10 | Low | The contract establishes a clear `auth` role for administrative functions, which is initialized to the deployer and can be managed via `rely` and `deny` (7.3 Access Control). This role controls… |
| **Upgrades** | 5/10 | Medium | The contract correctly implements the UUPS upgradeability pattern using OpenZeppelin's `UUPSUpgradeable` base contract (7.7 Upgrades). The `_authorizeUpgrade` function is appropriately overridden and… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 1 Low · ⚪ 8 Informational_

### `L-01` — `permit` Function Front-Running Vulnerability  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `permit` function, while correctly implemented according to EIP-2612, is inherently susceptible to front-running. A malicious actor could observe a pending `permit` transaction and submit their own transaction with a higher gas price, potentially causing the legitimate transaction to fail or consuming the `nonce` for a different `permit` call if they can craft a valid signature. While the `nonce` mechanism prevents replay attacks of the *same* signature, it does not prevent gas griefing or denial of service for the legitimate user (7.2 Code Security).

**Recommendation:** Users should be aware of the front-running risks associated with `permit` transactions. While the protocol cannot fully mitigate this inherent characteristic, providing clear warnings to users about potential gas griefing or allowance 'theft' for specific `permit` parameters can be beneficial.


### `I-01` — `_isValidSignature` Contract Check Edge Case  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_isValidSignature` function checks `signer.code.length > 0` to determine if an address is a contract before attempting an `IERC1271.isValidSignature` staticcall. This check can be bypassed during contract deployment if a contract calls `permit` within its constructor, as `signer.code.length` would still be zero. While this is a known edge case for `extcodesize` checks and unlikely to be exploited in the context of `permit` where `owner` is typically an EOA or a fully deployed contract, it's a subtle detail in contract interaction logic (7.2 Code Security).

**Recommendation:** No immediate action is required as the impact is minimal for the `permit` function's intended use. However, for future implementations involving `extcodesize` checks, consider alternative methods or acknowledge this specific edge case.


### `I-02` — Centralized Control of Critical Functions  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `auth` modifier grants a single address (or a set of addresses added via `rely`) complete control over critical functions such as `mint` (token supply inflation) and `_authorizeUpgrade` (contract logic changes). This centralization introduces a single point of failure and trust, as a compromise of this address could lead to arbitrary minting or malicious upgrades, severely impacting the stablecoin's integrity and user trust (7.3 Access Control, 7.4 Economic, 7.5 Governance, 7.7 Upgrades).

**Recommendation:** Implement a robust multi-signature wallet or a decentralized governance mechanism (e.g., a DAO) to manage the `auth` role. This would require multiple approvals for critical operations, significantly reducing the risk of a single point of compromise and distributing control.


### `I-03` — Missing Overflow Check in `mint` Function  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `mint` function uses `unchecked` blocks for `balanceOf[to] = balanceOf[to] + value` and `totalSupply = totalSupply + value`. While `uint256` is very large, in the extreme theoretical case where `totalSupply` or an individual `balanceOf` approaches `type(uint256).max`, adding `value` could lead to an overflow, wrapping the value to zero. Although highly improbable in practical scenarios for a stablecoin, explicit overflow checks or removal of `unchecked` for additions are generally safer, especially for functions that increase total supply (7.2 Code Security).

**Recommendation:** Re-evaluate the necessity of `unchecked` for additions in the `mint` function. If `unchecked` is desired for gas optimization, ensure that external safeguards or protocol invariants prevent `totalSupply` or `balanceOf` from reaching values close to `type(uint256).max` when `mint` is called. Alternatively, remove `unchecked` to rely on default Solidity 0.8+ overflow protection.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.2% of supply. What remains: 0.7% in wallets, 92.5% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as USDS (USDS), market cap $10.0B, rank #14. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $9.8M (DexScreener, all pools). 24h trading volume $477K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Stablecoin — issuer-backed (fiat reserves)  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Fiat-backed Stablecoin. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $9.8M of DEX liquidity across 22 pools. Launch: 709 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdc03...384f`](https://etherscan.io/address/0xdc035d45d973e3ec169d2276ddab16f1e407384f) |
| **Network** | Ethereum |
| **Price** | $0.9978 |
| **24h Volume** | $477.1K |
| **Liquidity** | $8.99M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 93.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 71 buys / 48 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x2621cc0b3f3c079c1db0e80794aa24976f0b9e3c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usds-stablecoin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
