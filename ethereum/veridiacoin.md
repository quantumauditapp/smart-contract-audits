---
token: veridiacoin
ticker: VC
network: ethereum
risk_score: 62
status: medium
date: 2026-09-30
---

# veridiacoin (VC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/veridiacoin-eth)

---

## Audit Summary

The RobinVistaToken contract, intended as a proxy implementation, contains a critical vulnerability related to its initialization function. The `initialize` function lacks proper access control, allowing any caller to become the designated 'factory' and mint the entire token supply to themselves. This flaw severely compromises the token's security, economic model, and intended operational control. While the contract utilizes well-audited OpenZeppelin ERC20 components, this fundamental design flaw in the initialization process poses an immediate and severe risk.

> **Final Recommendation:** It is critical to implement robust access control for the `initialize` function to ensure only authorized entities can perform the initial setup and token minting. This typically involves using an `initializer` modifier from OpenZeppelin's `UUPSUpgradeable` or `Initializable` contracts, or a custom `onlyOwner` or `onlyFactory` check. Additionally, review and remove any unused state variables (`deployer`, `metadataURI`) to optimize gas usage and improve code clarity. Ensure that the constructor of an implementation contract is empty or only sets `immutable` variables, as its state is not directly used by proxy instances.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages OpenZeppelin's robust ERC20 implementation, providing a solid foundation for token functionality and mitigating common integer overflow/underflow risks (7.2 Code Security).… |
| **Governance / Economics** | 1/10 | High | The economic model is severely compromised by the unprotected `initialize` function (7.4 Economic). An attacker can front-run the legitimate deployment, minting all tokens to their address and… |
| **Upgrades** | 2/10 | High | The contract is designed as an implementation for a proxy, which necessitates careful handling of initialization (7.7 Upgrades). The constructor's assignment of `factory = address(0xdead);` is… |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `C-01` — Unprotected Initialization Allows Token Hijack  *(Severity: Critical · Status: Unresolved)*

The `initialize` function, which is intended for initial setup of the token, lacks any access control. In a proxy deployment scenario, this means any external address can call `initialize` on the proxy contract. The first caller will become the `factory` address and will receive the entire `totalSupply_` of tokens, effectively hijacking the token's initial distribution and control. The constructor's assignment of `factory = address(0xdead);` does not protect the proxy's storage from this vulnerability.

**Recommendation:** Implement a robust access control mechanism for the `initialize` function. For proxy contracts, consider using OpenZeppelin's `UUPSUpgradeable` or `Initializable` base contracts which provide an `initializer` modifier. This modifier ensures the function can only be called once and by a designated address (e.g., the deployer or a governance contract).


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `L-01` — Unused State Variables  *(Severity: Low · Status: Unresolved)*

The state variables `deployer` and `metadataURI` are set during the `initialize` function call but are never subsequently read or used within the contract's logic. Storing these variables consumes unnecessary gas during deployment and each time `initialize` is called, without providing any functional benefit to the contract.

**Recommendation:** Remove the `deployer` and `metadataURI` state variables if they are not intended to be used by the contract's logic. If they are meant for off-chain consumption, consider emitting them as events during initialization instead of storing them on-chain to save gas.


### `I-01` — Inconsistent Constructor Logic for Proxy Implementation  *(Severity: Informational · Status: Unresolved)*

The constructor of `RobinVistaToken` sets `factory = address(0xdead);`. For an implementation contract used with a proxy, the constructor runs only once when the implementation itself is deployed, not when the proxy is initialized. The state variables of the implementation contract are not directly used by the proxy; instead, the proxy operates on its own storage. Therefore, setting `factory` in the constructor is misleading and irrelevant for the proxy's operational state, although in this specific case, it does not directly cause a vulnerability due to the `initialize` check (which itself is flawed).

**Recommendation:** Constructors for proxy implementation contracts should generally be empty or only set `immutable` variables. All mutable state initialization should occur within an `initialize` function, which is called via the proxy, to correctly set the proxy's storage.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 86.8% of supply. What remains: 6.9% in wallets, 79.9% in other contracts. 57 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

57 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $42K (DexScreener, all pools). 24h trading volume $70K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $42K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1165...ac04`](https://etherscan.io/address/0x116510fa1e99de5b2717426d064983d54aa4ac04) |
| **Network** | Ethereum |
| **Price** | $0.0001133 |
| **24h Volume** | $69.7K |
| **Liquidity** | $42.2K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 23h |
| **Top-10 Holders** | 86.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 107 buys / 50 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x56195fa1a4485e0c58b3af043797ead12a48c01f60d87c064928c3529a2b3559)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/veridiacoin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-30*
