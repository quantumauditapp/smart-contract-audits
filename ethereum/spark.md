---
token: Spark
ticker: SPK
network: ethereum
risk_score: 86
status: critical
date: 2026-09-14
---

# Spark (SPK) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 86/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spark-eth)

---

## Audit Summary

The SDAO token contract implements an ERC-20-like standard with EIP-2612 permit functionality and EIP-1271 signature validation. A critical vulnerability was identified in the `mint` function where `totalSupply` can overflow due to an unchecked arithmetic operation, leading to an incorrect total supply. Additionally, the contract exhibits high centralization risks due to a single `auth` role controlling token minting, burning, and metadata modification. Addressing these issues is paramount for the security and integrity of the token.

> **Final Recommendation:** Prioritize addressing the critical `totalSupply` overflow vulnerability in the `mint` function to prevent severe economic consequences. Implement robust access control mechanisms, such as a multi-signature wallet for the `auth` role, and consider separating administrative privileges to reduce the impact of a single compromised key. For critical functions like minting and metadata changes, evaluate the necessity of such centralized control and explore more decentralized or time-locked alternatives if appropriate for the protocol's long-term vision.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract implements an ERC-20-like token with EIP-2612 `permit` functionality and EIP-1271 signature validation. The `permit` implementation appears robust, correctly handling nonces and domain… |
| **Governance / Economics** | 1/10 | High | The token's economic model and governance are highly centralized, relying on a single `auth` role managed by the `wards` mapping. This role has extensive power, including the ability to mint tokens… |
| **Upgrades** | 1/10 | High | The contract is not designed to be upgradeable. This simplifies the architecture by avoiding the complexities and potential risks associated with proxy patterns. Any future changes to the contract… |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — `totalSupply` Overflow in `mint` function  *(Severity: Critical · Status: Unresolved)*

The `mint` function uses an `unchecked` block for the `totalSupply = totalSupply + value;` operation. If `totalSupply` is close to `type(uint256).max` and a large `value` is minted, `totalSupply` will overflow and wrap around to a small number. This breaks the fundamental invariant of token supply, leading to an incorrect total supply and potential economic exploits or system failures in protocols relying on the correct `totalSupply` value. (7.2 Code Security)

**Recommendation:** Remove the `unchecked` block around `totalSupply = totalSupply + value;` to allow default Solidity overflow checks to prevent this. Alternatively, implement a custom check `require(totalSupply + value >= totalSupply, 'SDAO/totalSupply-overflow');` before the addition.


### `H-01` — Centralized Control of Token Supply  *(Severity: High · Status: Unresolved)*

The `mint` function is controlled by addresses in the `wards` mapping via the `auth` modifier. This grants significant power to a small set of authorized addresses, allowing them to arbitrarily inflate the token supply. A compromise of an authorized address could lead to severe economic consequences, including hyperinflation and devaluation of the token. (7.3 Access Control, 7.4 Economic)

**Recommendation:** Implement a more decentralized or time-locked mechanism for minting, or clearly document the implications of this centralized control. Consider using a multi-signature wallet for the `auth` role to require multiple approvals for critical actions.


### `H-02` — Centralized Control of Token Metadata  *(Severity: High · Status: Unresolved)*

The `file` function allows authorized addresses (those in `wards`) to change the token `name` and `symbol`. While not directly impacting token value, this can lead to confusion, misrepresentation, and potential phishing if malicious names/symbols are set. This could undermine user trust and disrupt integrations with exchanges or other protocols. (7.3 Access Control, 7.4 Economic)

**Recommendation:** Remove the ability to change `name` and `symbol` after deployment, or implement a robust governance mechanism (e.g., time-locked multi-sig or DAO vote) for such critical changes.


### `M-01` — Lack of Granular Access Control  *(Severity: Medium · Status: Unresolved)*

The `auth` modifier provides an 'all-or-nothing' access control mechanism. Any address added to `wards` gains control over all privileged functions, including `mint`, `rely`, `deny`, and `file`. This lack of role separation increases the risk profile, as a single compromised `auth` key could lead to a full compromise of the token's administrative functions. (7.3 Access Control, 7.5 Governance)

**Recommendation:** Implement a more granular role-based access control (RBAC) system, assigning specific permissions (e.g., `MINTER_ROLE`, `ADMIN_ROLE`, `METADATA_EDITOR_ROLE`) to different addresses or multi-signature wallets.


### `L-01` — `permit` Function Overload Redundancy  *(Severity: Low · Status: Unresolved)*

The contract provides two `permit` functions: one accepting `bytes memory signature` and another accepting `uint8 v, bytes32 r, bytes32 s`. The latter simply encodes `v, r, s` into `bytes memory signature` and calls the first `permit` function. While functional, this adds a slight, unnecessary gas overhead for users who already have `v, r, s` separated, as the encoding step is redundant. (7.2 Code Security)

**Recommendation:** Consider having the `permit` function taking `v, r, s` directly process the signature without re-encoding, or remove the overloaded function if the `bytes memory signature` version is sufficient for all use cases.


### `I-01` — `DOMAIN_SEPARATOR` Recalculation on Chain ID Mismatch  *(Severity: Informational · Status: Unresolved)*

The `DOMAIN_SEPARATOR()` view function and the `permit` function recalculate the EIP-712 domain separator if `block.chainid` differs from `deploymentChainId`. While this design choice offers flexibility for potential cross-chain deployments or forks, it introduces a minor gas overhead for `permit` calls executed on a chain ID different from the deployment chain. For a token primarily intended for a single, fixed chain, this recalculation might be an unnecessary complexity and gas cost. (7.1 Architecture, 7.2 Code Security)

**Recommendation:** Document this design choice and its implications. If the token is strictly intended for a single chain, consider simplifying the `DOMAIN_SEPARATOR` logic to always return the immutable `_DOMAIN_SEPARATOR` to save gas.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc200...b066`](https://etherscan.io/address/0xc20059e0317de91738d13af027dfc4a50781b066) |
| **Network** | Ethereum |
| **Price** | $0.01879 |
| **24h Volume** | $64.6K |
| **Liquidity** | $758.2K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 86.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 64 buys / 129 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x39f748f252ffff5f2cb755824bd46bd4c0720ffcec1ed128b38a1049a0e70496)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spark-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-14*
