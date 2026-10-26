---
token: Frax USD
ticker: FRXUSD
network: ethereum
risk_score: 9
status: low
date: 2026-09-02
---

# Frax USD (FRXUSD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/frax-usd-eth)

---

## Audit Summary

The audit of the FrxUSD token contract, an ERC-20 implementation utilizing a TransparentUpgradeableProxy, identified a critical vulnerability related to its constructor initialization. The implementation contract's owner is incorrectly set to address(1) due to constructor logic, rendering all owner-restricted functions inaccessible to the legitimate proxy owner. Additionally, the contract exhibits a high degree of centralization with extensive owner and freezer privileges, and the owner can bypass pause and freeze mechanisms. While the contract leverages well-vetted OpenZeppelin libraries for core functionality and EIP standards, the upgradeability and access control flaws pose significant risks.

> **Final Recommendation:** Immediately address the critical constructor issue by deploying a new implementation contract that correctly initializes the `Ownable` role via an `initialize` function, rather than the constructor. Review and potentially restrict the extensive centralized powers of the owner and freezer roles, considering multi-signature requirements for sensitive operations or time-locks. Improve the `removeMinter` function to efficiently remove elements from the `minters_array` to prevent unbounded growth and potential gas issues.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The technical architecture benefits from inheriting battle-tested OpenZeppelin contracts (ERC20, ERC20Permit, Ownable2Step) and implementing EIP-3009 and EIP-2612 for enhanced token utility (7.1… |
| **Governance / Economics** | 9/10 | Low | The contract design grants significant centralized control to the owner and designated freezers (7.5 Governance). The owner can add/remove minters and freezers, pause/unpause transfers, and burn… |
| **Upgrades** | 5/10 | Medium | The contract is deployed behind a TransparentUpgradeableProxy, but the implementation contract's constructor in `FrxUSD3` initializes `Ownable` with `address(1)` (7.7 Upgrades). This is a critical… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Other-Contract |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 68.0% |
| **Top-3 Unlocked** | ⚠️ 90.8% |

## Security Findings

_⚪ 10 Informational_

### `I-01` — Informational: Use of `address(1)` in Constructor  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The constructor of `FrxUSD3` initializes the `Ownable` contract with `address(1)` as the owner. While the primary issue is the use of a constructor for initialization in an upgradeable contract (C-01), the specific choice of `address(1)` is unusual. This address is a valid, but generally unused, Ethereum address. Its use here might be confusing or lead to misinterpretations if not clearly documented as a placeholder or a symptom of the upgradeability issue.

**Recommendation:** Ensure that any placeholder addresses or unusual initialization values are thoroughly documented within the code or in external specifications to prevent confusion or misinterpretation by future auditors or developers.


### `I-02` — Informational: OpenZeppelin Contracts Version 5.3.0  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract utilizes OpenZeppelin Contracts version 5.3.0. This is a relatively recent version, indicating a commitment to using up-to-date and potentially more secure library components. However, newer versions can sometimes introduce subtle behavioral changes or require careful integration. It's important to ensure that the development team is fully aware of any breaking changes or new features introduced in this version compared to previous ones they might have used.

**Recommendation:** Maintain a clear understanding of the OpenZeppelin Contracts changelog for version 5.3.0 and ensure all integrations are compatible. Regularly review OpenZeppelin's security advisories and consider upgrading to the latest stable version as new releases become available, after thorough testing.


### `I-03` — Critical: Constructor Initialization in Upgradeable Contract Locks Out Owner  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `FrxUSD3` contract, which serves as the implementation for a TransparentUpgradeableProxy, initializes its `Ownable` base contract via its constructor: `constructor() FrxUSD2(address(1), "Frax USD", "frxUSD") {}`. In an upgradeable proxy pattern, the constructor of the implementation contract is called only once when the implementation is deployed, not when the proxy is initialized. This means the `owner` state variable within the implementation contract is permanently set to `address(1)`. Consequently, any function protected by the `onlyOwner` modifier will only be callable by `address(1)`, rendering the legitimate

**Recommendation:** For upgradeable contracts, avoid using constructors for state initialization. Instead, implement an `initialize` function (e.g., `function initialize(address _ownerAddress, string memory _name, string memory _symbol) public initializer`) that is called once by the proxy's admin after deployment. This function should set the owner and other initial parameters. Ensure the `initialize` function uses an `initializer` modifier (e.g., from OpenZeppelin's `UUPSUpgradeable` or `Initializable`) to preve…


### `I-04` — High: Extensive Centralized Control by Owner and Freezers  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract grants significant centralized control to the `owner` and designated `freezer` roles. The owner has the power to add/remove minters, add/remove freezers, pause/unpause all transfers, and burn arbitrary amounts of tokens from any address, including burning an entire balance if `_amount` is zero. Freezers can freeze/thaw any user account. This high degree of centralization means that a compromise of the owner's or a freezer's private keys could lead to severe consequences, including censorship, denial of service, or arbitrary token destruction.

**Recommendation:** While some centralization is inherent in stablecoin designs, consider implementing additional safeguards. For critical functions like `burnMany`, `addMinter`, `removeMinter`, `addFreezer`, `removeFreezer`, `pause`, and `unpause`, consider adding time-locks to allow users to react to pending changes. Implement multi-signature requirements for all sensitive administrative actions if not already enforced at the owner wallet level. Clearly document the responsibilities and security procedures for m…


### `I-05` — Medium: Owner Bypasses Pause and Freeze Checks  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_update` internal function, which is called during token transfers, includes a conditional check: `if (msg.sender != owner()) { ... }`. This logic allows the contract owner to bypass the `isPaused` and `isFrozen` checks. While this might be intended for emergency recovery or specific administrative actions, it means the owner is not subject to the same restrictions as other users. This could be perceived as a backdoor, potentially allowing the owner to transfer tokens even when the contract is paused or to/from frozen accounts, undermining the intended universal application of these security mechanisms.

**Recommendation:** Re-evaluate the necessity of the owner bypassing pause and freeze checks. If this functionality is critical for emergency scenarios, ensure it is clearly documented and understood. Consider implementing a separate, explicitly named emergency function for owner-initiated transfers that bypasses these checks, rather than embedding it within the general `_update` logic. This would make the intent clearer and reduce the risk of unintended use.


### `I-06` — Low: Inefficient Minter Removal in `minters_array`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `removeMinter` function iterates through the `minters_array` to find the target address and sets `minters_array[i] = address(0)`. This approach does not actually remove the element from the array; it merely marks it as `address(0)`. Over time, if many minters are added and removed, the `minters_array` will grow indefinitely with `address(0)` entries. This can lead to increased gas costs for any future function that iterates over this array, and could potentially hit block gas limits if the array becomes excessively large.

**Recommendation:** To efficiently remove elements from a dynamic array, consider using a 'swap and pop' pattern. When an element is to be removed, swap it with the last element in the array and then `pop()` the last element. This maintains array contiguity and avoids `address(0)` entries. Alternatively, if the order of minters is not critical, a `mapping(address => bool)` for `minters` is sufficient for checking membership, and `minters_array` could be removed or rebuilt periodically if iteration is truly necessa…


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 85.6% of supply. What remains: 44.3% in wallets, 41.2% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Frax USD (FRXUSD), market cap $100M, rank #277. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $28.4M (DexScreener, all pools). 24h trading volume $1.9M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Stablecoin — issuer-backed (fiat reserves)  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Fiat-backed Stablecoin. Tokenomics — Supply: fixed — the contract has no mint function. Control: a 4-of-7 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $28.4M of DEX liquidity across 13 pools. Launch: 420 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcacd...6e29`](https://etherscan.io/address/0xcacd6fd266af91b8aed52accc382b4e165586e29) |
| **Network** | Ethereum |
| **Price** | $0.9999 |
| **24h Volume** | $1.86M |
| **Liquidity** | $14.77M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 85.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 89 buys / 32 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x13e12bb0e6a2f1a3d6901a59a9d585e89a6243e1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/frax-usd-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
