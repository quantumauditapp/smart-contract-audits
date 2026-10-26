---
token: Circle Internet Group Inc.
ticker: CRCLB
network: bsc
risk_score: 12
status: low
date: 2026-09-23
---

# Circle Internet Group Inc. (CRCLB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/circle-internet-group-inc-bsc)

---

## Audit Summary

The audit of the SecuritiesToken contract, deployed as an upgradeable Beacon Proxy on BSC, reveals a well-structured token implementation utilizing OpenZeppelin's upgradeable patterns and custom ERC8056 scaling logic. The contract incorporates robust access control, compliance, and pausing mechanisms. Key findings include a critical initialization vulnerability that could lead to administrative lockout, and significant economic control vested in the ISSUER_ROLE. While the upgradeability model is sound, the high degree of centralization in administrative and issuer roles necessitates careful management of privileged keys.

> **Final Recommendation:** Prioritize addressing the critical initialization vulnerability by implementing robust input validation for the `admin_` address to prevent accidental lockout of administrative control. Carefully review the distribution of powers, particularly the `ISSUER_ROLE`'s ability to authorize `uiMultiplier` changes, and consider if this level of control aligns with the intended trust model and risk appetite. Ensure that the `issuers_` array size is managed to avoid gas limit issues during deployment, potentially by implementing a batched role granting mechanism if many issuers are anticipated.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract leverages OpenZeppelin's upgradeable patterns and Solidity 0.8.x, benefiting from built-in overflow/underflow protection and secure ERC-20 implementations (7.2 Code Security). The… |
| **Governance / Economics** | 9/10 | Low | The `SecuritiesToken` implements a robust role-based access control system using `AccessControlEnumerableUpgradeable`, defining `DEFAULT_ADMIN_ROLE` and `ISSUER_ROLE`. The `DEFAULT_ADMIN_ROLE` holds… |
| **Upgrades** | 5/10 | Medium | The contract is designed for upgradeability, inheriting from OpenZeppelin's upgradeable contracts and correctly using `_disableInitializers()` in the constructor and an `initializer` function. The… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 35.7% |
| **Top-3 Unlocked** | 72.1% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `M-01` — Gas Limit Risk for `issuers_` Array in `initialize`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function iterates through the `issuers_` array to grant the `ISSUER_ROLE` to each address. If this array contains an excessively large number of addresses, the transaction to initialize the contract could exceed the block gas limit. This would prevent the contract from being successfully deployed and initialized, leading to operational failure.

**Recommendation:** Limit the maximum size of the `issuers_` array passed during initialization. If a large number of issuers is anticipated, consider implementing a separate, batched function callable by the `DEFAULT_ADMIN_ROLE` after initialization to grant roles incrementally, or use a more gas-efficient method for initial role assignment.


### `M-03` — Broad Powers of `ISSUER_ROLE` to Affect Token Value  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ISSUER_ROLE` has the ability to mint, burn, and crucially, authorize changes to the `uiMultiplier` via the `_authorizeMultiplierUpdate` function. The `uiMultiplier` directly impacts the effective value of the token, as it scales user balances. While the `DEFAULT_ADMIN_ROLE` manages `ISSUER_ROLE` assignments and the multiplier has defined bounds (`1e9` to `1e27`), granting this significant economic control to a potentially broader set of `ISSUER_ROLE` holders increases the attack surface for economic manipulation or misuse compared to restricting it solely to the `DEFAULT_ADMIN_ROLE`.

**Recommendation:** Re-evaluate if the `ISSUER_ROLE` should have the authority to authorize `uiMultiplier` updates. Consider restricting this specific power solely to the `DEFAULT_ADMIN_ROLE` to centralize control over the token's value scaling, or implement a multi-signature scheme for such critical operations. Ensure robust processes for managing `ISSUER_ROLE` assignments.


### `L-01` — High Reliance on External Contracts  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `SecuritiesToken` contract heavily relies on external contracts, specifically `ComplianceClientUpgradeable` and `PauseManagerClientUpgradeable`. The security, availability, and correct functioning of these external contracts are critical to the `SecuritiesToken`'s operation, including transfer restrictions and pausing capabilities. Any vulnerability, compromise, or malicious action within these external contracts could directly impact the functionality and security of the token.

**Recommendation:** Ensure that the external `ComplianceClient` and `PauseManagerClient` contracts are thoroughly audited, well-maintained, and secured. Implement robust monitoring for these external dependencies. Consider adding circuit breakers or emergency mechanisms in the `SecuritiesToken` to mitigate risks if an integrated external contract becomes compromised or malfunctions.


### `I-01` — Centralized Control of `DEFAULT_ADMIN_ROLE`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` holds extensive power over the contract, including managing all roles (granting/revoking `ISSUER_ROLE`), setting critical external contracts (compliance, pause manager), enabling/disabling core token functionalities like minting and burning, and changing token metadata (name, symbol, identifier). While common for managed tokens, this high degree of centralization represents a significant single point of failure and trust assumption, as a compromise of the admin key could lead to severe consequences.

**Recommendation:** Implement robust security measures for the `DEFAULT_ADMIN_ROLE` key, such as multi-signature wallets (e.g., Gnosis Safe) and strict operational procedures. Consider decentralizing certain administrative functions over time or introducing time-locks for critical changes to reduce immediate impact of a compromise.


### `I-02` — Unchecked `admin_` address in `initialize`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function grants the `DEFAULT_ADMIN_ROLE` to the `admin_` address provided as an argument. If `admin_` is set to `address(0)`, the `DEFAULT_ADMIN_ROLE` will be assigned to the zero address. This would effectively lock out all administrative control over the contract, making it unmanageable and potentially bricking critical functionalities that rely on the `DEFAULT_ADMIN_ROLE`.

**Recommendation:** Implement a check in the `initialize` function to ensure that the `admin_` address is not `address(0)`. For example: `require(admin_ != address(0), "SecuritiesToken: Admin cannot be zero address");`


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 96.0% of supply. What remains: 93.7% in wallets, 2.3% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Circle Internet Group (bStocks Tokenized Stock) (CRCLB), market cap $152M, rank #208. Its admin (0x45e3…679d) controls 100 issuer-backed coins CoinGecko lists on bsc, $1.2B together, among them SpaceX (bStocks Tokenized Stock), SanDisk (bStocks Tokenized Stock), Semicon Bull 3X ETF (bStocks Tokenized ETF): one issuer's programme, read on-chain. Verified by: CoinGecko, issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.1M (DexScreener, all pools). 24h trading volume $3.7M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $1.1M of DEX liquidity across 7 pools. Launch: 47 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x80f3...ffc0`](https://bscscan.com/address/0x80f3d493ebce97e343c53d29a137942416b4ffc0) |
| **Network** | BNB Chain |
| **Price** | $94.1000 |
| **24h Volume** | $3.70M |
| **Liquidity** | $1.11M |
| **Volume / Liquidity** | 3.3× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 96.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9938 buys / 10176 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x29967c54c5bf12e8158c8894376064b30ebab297)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/circle-internet-group-inc-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-23*
