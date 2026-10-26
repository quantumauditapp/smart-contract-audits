---
token: USDe
ticker: USDE
network: ethereum
risk_score: 12
status: low
date: 2026-09-02
---

# USDe (USDE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usde-eth)

---

## Audit Summary

The USDe contract implements an ERC20 token with burnable and permit functionalities, utilizing OpenZeppelin's Ownable2Step for ownership management. A key feature is the `minter` role, which is exclusively authorized to mint new tokens. The contract's security is enhanced by using battle-tested OpenZeppelin libraries and a Timelock for the owner address. However, the centralized control over token supply via the `minter` and `owner` roles introduces significant economic and governance risks, as the token's stability relies heavily on the integrity of these privileged accounts and associated off-chain processes.

> **Final Recommendation:** Prioritize the robust security of the `minter` and `owner` private keys, implementing multi-signature wallets and stringent operational procedures. Ensure transparency regarding the off-chain collateralization and redemption mechanisms that back the USDe token. While the contract code is sound, the primary risks stem from the centralized control points and their associated operational security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The USDe contract demonstrates strong technical security (7.2 Code Security) by inheriting from well-audited OpenZeppelin contracts (ERC20, ERC20Burnable, ERC20Permit, Ownable2Step). The code is… |
| **Governance / Economics** | 9/10 | Low | The contract's economic model (7.4 Economic) and governance (7.5 Governance) are highly centralized. The `minter` role has unlimited power to mint tokens, making the token's supply and value entirely… |
| **Upgrades** | 10/10 | Low | The USDe contract is not designed as an upgradeable proxy (7.7 Upgrades). This means there are no upgrade-related risks such as proxy implementation vulnerabilities or storage collisions. However, it… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 59.1% |
| **Top-3 Unlocked** | ⚠️ 88.0% |

## Security Findings

_⚪ 9 Informational_

### `I-01` — Implied Off-Chain Collateralization  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract's minting mechanism is permissioned but does not include any on-chain checks or enforcement for collateralization (7.4 Economic, 7.6 External). The stability and value of USDe are implicitly reliant on off-chain reserves and operational procedures managed by the protocol, which are not auditable within the smart contract code. Users must trust the issuer's commitment to maintain the peg through external means.

**Recommendation:** Clearly communicate the off-chain collateralization strategy, audit reports of reserves, and redemption mechanisms to users. While not a smart contract vulnerability, transparency regarding the external dependencies is crucial for user confidence and understanding of the token's economic model.


### `I-02` — Centralized Control over Token Supply  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `minter` address has the exclusive and unlimited ability to mint new USDe tokens. This centralized control (7.3 Access Control, 7.4 Economic) means that the token's supply and value are highly dependent on the security and integrity of the `minter`'s private keys and the underlying off-chain collateralization mechanism. A compromise of the `minter` address would allow an attacker to mint arbitrary amounts of tokens, leading to severe inflation and loss of value.

**Recommendation:** Implement robust security measures for the `minter` address, such as a multi-signature wallet with a high threshold, hardware security modules (HSMs), and strict operational controls. Regularly review and audit the processes surrounding the `minter`'s operations and the off-chain collateral management (7.8 Operations).


### `I-03` — Owner's Authority to Change Minter  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract owner has the authority to change the `minter` address via the `setMinter` function (7.3 Access Control). While the owner is a Timelock (7.8 Operations), this still grants significant control over the token's core functionality. A malicious or compromised owner could assign a new `minter` to an attacker-controlled address, effectively taking over the minting capability.

**Recommendation:** Ensure the Timelock controlling the owner address has a sufficiently long delay and is managed by a decentralized or highly secure governance process (7.5 Governance). Consider implementing additional checks or a multi-signature requirement for critical owner actions like `setMinter` if the current Timelock setup is deemed insufficient.


### `I-04` — Ownership Renunciation Disabled  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `renounceOwnership` function is explicitly overridden to revert, preventing the owner from relinquishing control of the contract (7.3 Access Control). While this prevents accidental renunciation, it also means the owner role can never be permanently removed from the contract, which might be a desired feature for protocols aiming for full decentralization. For a centralized stablecoin, this is likely an intentional design choice to maintain oversight.

**Recommendation:** Confirm that preventing ownership renunciation aligns with the long-term decentralization goals of the USDe protocol. If future decentralization is a goal, consider a mechanism to transfer ownership to a zero address or a community-controlled contract, or to enable renunciation, possibly after a significant transition period.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 95.0% of supply. What remains: 9.7% in wallets, 85.3% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Ethena USDe (USDE), market cap $4.6B, rank #23. Its owner (0xe8dc…7c94) controls 3 issuer-backed coins CoinGecko lists on ethereum, $6.0B together, among them Ethena Staked USDe, Ethena Staked ENA: one issuer's programme, read on-chain. Verified by: CoinGecko, issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $65.8M (DexScreener, all pools). 24h trading volume $99K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — a timelock with a 24h delay — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Stablecoin — issuer-backed (fiat reserves)  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Fiat-backed Stablecoin. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: a timelock with a 24h delay. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $65.8M of DEX liquidity across 18 pools. Launch: 990 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4c9e...68b3`](https://etherscan.io/address/0x4c9edd5852cd905f086c759e8383e09bff1e68b3) |
| **Network** | Ethereum |
| **Price** | $0.9999 |
| **24h Volume** | $99.0K |
| **Liquidity** | $34.04M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 2y |
| **Top-10 Holders** | 95.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 160 buys / 88 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x5dc1bf6f1e983c0b21efb003c105133736fa0743)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usde-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
