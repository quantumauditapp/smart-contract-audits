---
token: Uniswap
ticker: UNI
network: ethereum
risk_score: 57
status: high
date: 2026-06-16
---

# Uniswap (UNI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 57/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/uniswap-eth)

---

## Audit Summary

The Uni contract implements an ERC-20 token with governance delegation and a controlled minting mechanism. The contract correctly utilizes OpenZeppelin's SafeMath library to prevent integer overflows/underflows, which is appropriate for its Solidity version. A key centralization risk exists with the `minter` role, which has significant control over token supply, albeit with defined limits. The contract is not upgradeable, ensuring immutability.

> **Final Recommendation:** It is recommended to consider migrating to a newer Solidity compiler version (e.g., 0.8.x) in future iterations to leverage built-in overflow checks and other language improvements. The `minter` role, which currently holds significant power, should ideally be controlled by a robust multi-signature wallet or a decentralized governance mechanism to mitigate centralization risks and enhance security. Regular security reviews of the `minter`'s operational procedures are also advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good code security practices by using OpenZeppelin's `SafeMath` library to prevent arithmetic overflows/underflows (7.2 Code Security). The implementation of ERC-20, EIP-712… |
| **Governance / Economics** | 1/10 | High | The contract incorporates a robust governance delegation system, allowing token holders to delegate their voting power, which is a strength for decentralized decision-making (7.5 Governance).… |
| **Upgrades** | 5/10 | Medium | The contract is not designed with an upgrade mechanism (e.g., proxy pattern), meaning its logic is immutable once deployed (7.7 Upgrades). This eliminates upgrade-related risks such as proxy… |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Minter Role  *(Severity: High · Status: Unresolved)*

The `minter` address has the sole authority to mint new tokens, subject to `mintCap` and time constraints. This represents a significant centralization risk (7.3 Access Control, 7.4 Economic). If the `minter`'s private key is compromised, an attacker could inflate the token supply up to the `mintCap` per year, devaluing existing tokens. The `setMinter` function allows the current minter to transfer this critical role, which is also a high-privilege operation.

**Recommendation:** Consider decentralizing the `minter` role by assigning it to a robust multi-signature wallet (e.g., Gnosis Safe) or a community-governed smart contract. This would require multiple approvals for minting operations or role transfers, significantly reducing the risk of a single point of failure.


### `L-01` — Potential High Gas Costs for Checkpoints  *(Severity: Low · Status: Unresolved)*

The `_writeCheckpoint` function stores historical vote data for each account. While necessary for the governance delegation mechanism, if an account frequently delegates or transfers tokens, the `numCheckpoints` for that address could grow very large. This could lead to increased gas costs for subsequent `_writeCheckpoint` operations or for reading historical vote data (7.8 Operations).

**Recommendation:** While this is an inherent design choice for Compound-style governance, consider monitoring the growth of `numCheckpoints` for highly active addresses. For future iterations, explore alternative checkpointing strategies or gas optimization techniques if this becomes a significant operational burden.


### `I-01` — Older Solidity Compiler Version  *(Severity: Informational · Status: Unresolved)*

The contract is compiled with Solidity version `^0.5.16`. While `SafeMath` is correctly used to prevent integer overflows/underflows, newer Solidity versions (e.g., 0.8.x) include built-in overflow/underflow checks by default, making external libraries like `SafeMath` largely redundant and potentially saving gas (7.2 Code Security). Newer compilers also offer additional language features and security improvements.

**Recommendation:** For future contract deployments or upgrades, consider migrating to a more recent Solidity compiler version (e.g., 0.8.x). This would allow for the removal of `SafeMath` library calls, simplifying the code and potentially reducing gas costs, while benefiting from the latest compiler optimizations and security features.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1f98...f984`](https://etherscan.io/address/0x1f9840a85d5af5bf1d1762f925bdaddc4201f984) |
| **Network** | Ethereum |
| **Price** | $3.0074 |
| **24h Volume** | $2.04M |
| **Liquidity** | $12.31M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 5y |
| **Top-10 Holders** | 52.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 608 buys / 540 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Uniswap a scam?

Based on the data, Uniswap (UNI) does not exhibit typical scam characteristics; its contract is verified, and no mint function exists, preventing arbitrary supply inflation. However, non-renounced ownership and significant token concentration (52.3% by top 10 holders) introduce centralization risks. While these contribute to its 'High Risk' score of 68/100 and warrant caution, they do not inherently categorize Uniswap as a scam.

### Is Uniswap safe to buy?

UNI carries a 'High Risk' score (68/100) due to several factors. Contract ownership is not renounced, and liquidity is unlocked, raising concerns about administrative control over token parameters or market stability. Additionally, 52.3% of the supply is concentrated among the top 10 holders. These factors suggest potential for centralized influence, meaning investors should exercise elevated caution and conduct thorough due diligence.

### Has Uniswap been audited?

The Uniswap (UNI) contract is verified, meaning its deployed bytecode matches the publicly available source code. This offers transparency for community review. However, contract verification differs from a comprehensive security audit, which involves expert analysis to identify vulnerabilities and logic flaws. The provided data confirms verification but does not explicitly indicate a full security audit has been performed.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x1d42064fc4beb5f8aaf85f4617ae8b3b5b8bd801)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/uniswap-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-16*
