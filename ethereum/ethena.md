---
token: Ethena
ticker: ENA
network: ethereum
risk_score: 100
status: critical
date: 2026-06-11
---

# Ethena (ENA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ethena-eth)

---

## Audit Summary

This report details the security audit of the ENA token contract, which serves as the governance token for the Ethena protocol. The contract is an ERC20 token with burnable and permit functionalities, inheriting from OpenZeppelin's Ownable2Step for robust access control. Key features include a controlled annual minting mechanism and a significant initial token distribution. The audit identified a High-severity issue related to centralized minting authority, two Medium-severity issues concerning initial supply distribution and reliance on block.timestamp, and several Low/Informational findings. The overall risk level is assessed as Medium, primarily due to the centralized control over token supply inflation.

> **Final Recommendation:** It is recommended to implement robust multi-signature or time-locked controls for the contract owner address, especially given its centralized minting authority. This would significantly mitigate the risk associated with a single point of failure. Additionally, ensure that the `_treasury` and `_foundation` addresses receiving the initial token supply are secured with strong operational controls, preferably multi-signature wallets, to protect the substantial token holdings. While `block.timestamp` is generally acceptable for yearly cooldowns, consider the implications for any future time-sensitive operations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The ENA contract demonstrates good technical architecture (7.1) by extending well-audited OpenZeppelin libraries for ERC20, burnable, permit, and two-step ownership functionalities. Code security… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) features a controlled inflation mechanism where the contract owner can mint new tokens annually, capped at 10% of the total supply. This centralized minting authority (7.5)… |
| **Upgrades** | 2/10 | High | The ENA token contract is not designed to be upgradeable (7.7). This means its logic is immutable once deployed, eliminating upgrade-related risks such as proxy implementation vulnerabilities or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 63.5% |
| **Top-3 Unlocked** | ⚠️ 95.2% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 3 Informational_

### `H-01` — Centralized Minting Authority  *(Severity: High · Status: Unresolved)*

The `mint` function is restricted to the contract owner via the `onlyOwner` modifier. This allows the owner to inflate the token supply annually up to `MAX_INFLATION` (10% of total supply). While limits are in place, this centralizes significant control over the token's economic policy in a single entity. A compromise of the owner's private key or malicious action by the owner could lead to uncontrolled inflation, devaluing the token.

**Recommendation:** Implement a robust multi-signature wallet or a decentralized autonomous organization (DAO) for the contract owner address. This would distribute control and require multiple approvals for critical operations like minting, significantly reducing the risk of a single point of failure or malicious unilateral action.


### `M-01` — Reliance on `block.timestamp` for Critical Cooldown  *(Severity: Medium · Status: Unresolved)*

The `MINT_WAIT_PERIOD` (365 days) relies on `block.timestamp` to enforce the yearly minting cooldown. While miner manipulation of `block.timestamp` is typically limited to small deviations to avoid network rejection, it is not entirely immune to manipulation. For a yearly cooldown, the impact is generally low, but it's a general pattern to be aware of for time-sensitive operations.

**Recommendation:** For a yearly cooldown, `block.timestamp` is often considered acceptable. However, for future critical time-sensitive operations, consider using a decentralized oracle service (e.g., Chainlink Keepers or a dedicated time oracle) to provide a more robust and less manipulable time source.


### `M-02` — Significant Initial Supply Distribution to Specific Addresses  *(Severity: Medium · Status: Unresolved)*

The constructor mints a substantial initial supply of 15 billion tokens to `_treasury` and `_foundation` addresses. The security and operational controls around these addresses are critical. If these are externally owned accounts (EOAs), they represent a single point of failure. If they are multi-signature wallets, their security depends on the configuration and key management practices.

**Recommendation:** Ensure that the `_treasury` and `_foundation` addresses are secured with robust operational controls, ideally multi-signature wallets with a sufficient number of signers and proper key management procedures. Regularly audit the security practices surrounding these critical addresses.


### `L-01` — Inflexible Inflation Rate  *(Severity: Low · Status: Unresolved)*

The `MAX_INFLATION` is defined as a `constant` (10%), meaning it cannot be modified after contract deployment. While this provides predictability for token holders, it removes the flexibility to adjust the inflation rate in response to future economic conditions or evolving protocol needs. This is a design choice that trades adaptability for certainty.

**Recommendation:** This is a design decision. If future flexibility is desired, consider making `MAX_INFLATION` a state variable that can be updated by the owner or a governance mechanism, potentially with a time-lock or multi-signature approval for changes.


### `I-01` — Efficient `uint40` Usage for Timestamp  *(Severity: Informational · Status: Resolved)*

The `lastMintTimestamp` variable is declared as `uint40`. This is an efficient use of storage compared to `uint256` for storing timestamps, as `uint40` is sufficient to store Unix timestamps for many centuries, leading to gas savings.

**Recommendation:** No action required. This is a good practice for gas optimization.


### `I-02` — Robust Ownership Transfer Mechanism  *(Severity: Informational · Status: Resolved)*

The contract utilizes OpenZeppelin's `Ownable2Step` for ownership transfers. This mechanism requires a two-step process (propose and accept), significantly reducing the risk of accidental ownership loss during transfer, which is a common vulnerability in `Ownable` contracts.

**Recommendation:** No action required. This is a good security practice.


### `I-03` — Prevention of Ownership Renunciation  *(Severity: Informational · Status: Resolved)*

The `renounceOwnership` function is explicitly overridden to revert, preventing the owner from accidentally or maliciously relinquishing control of the contract. This is a good security practice for contracts with critical owner-controlled functions.

**Recommendation:** No action required. This is a good security practice.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x57e1...6061`](https://etherscan.io/address/0x57e114b691db790c35207b2e685d4a43181e6061) |
| **Network** | Ethereum |
| **Price** | $0.07599 |
| **24h Volume** | $1.42M |
| **Liquidity** | $2.88M |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 61.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 380 buys / 489 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x8c52de694f5a4ce27ea85fe4bc47e08d22c5dfb5f9b38b2a63765ed52cd3b147)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ethena-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-11*
