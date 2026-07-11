---
token: Uniswap
ticker: UNI
network: ethereum
risk_score: 72
status: critical
date: 2026-06-16
---

# Uniswap (UNI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 72/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/uniswap-eth)

---

## Audit Summary

The audit of the Uni token contract revealed a robust implementation of ERC-20 standards with added governance features. Strengths include the use of OpenZeppelin's SafeMath library and EIP-712 for gasless transactions. However, significant centralization risk exists with the 'minter' role, which can control token supply and bypass minting cooldowns. The contract's non-upgradeable nature and use of an older Solidity compiler version also contribute to the overall risk profile.

> **Final Recommendation:** The Uni contract demonstrates a solid foundation for an ERC-20 token with governance capabilities. Addressing the identified high-severity centralization risks, particularly around the 'minter' role's ability to bypass cooldowns, is paramount. While non-upgradeability is a design choice, the project should be aware of its implications for long-term maintenance and bug fixes. Consider implementing a multi-signature wallet or a time-locked contract for critical administrative functions like `setMinter` and `setMintingAllowedAfter` to mitigate centralization risks.

For enhanced security and ongoing monitoring, a Premium Deploy option is recommended. This service provides continuous threat monitoring, incident response planning, and regular security reviews post-deployment, ensuring the protocol remains resilient against evolving threats and operational challenges.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture (7.1 Architecture) is well-structured, leveraging established patterns for ERC-20 and governance delegation. Code security (7.2 Code Security) is enhanced by the use of… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4 Economic) incorporates a minting cap and a minimum time between mints, providing some control over supply inflation. The governance mechanism (7.5 Governance) uses a standard… |
| **Upgrades** | 5/10 | Medium | The contract is designed as non-upgradeable (7.7 Upgrades), which simplifies its architecture by avoiding proxy complexities. However, this design choice introduces a high operational risk (7.8… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Minter Role with Significant Power  *(Severity: High · Status: Unresolved)*

The `minter` address has extensive control over the token supply, including the ability to mint new tokens and transfer the `minter` role to any address. While there are `mintCap` and `minimumTimeBetweenMints` restrictions, a compromised or malicious `minter` could still significantly impact the token's economic stability by inflating the supply up to the cap. This represents a single point of failure for token supply management.

**Recommendation:** Implement a multi-signature wallet or a time-locked contract for the `minter` role. For critical functions like `setMinter`, consider a governance-controlled mechanism or a multi-step transfer process with a delay to allow community oversight and intervention.


### `H-02` — Minter Can Bypass Minting Cooldown  *(Severity: High · Status: Unresolved)*

The `setMintingAllowedAfter` function allows the `minter` to set an arbitrary timestamp for when minting is allowed. A malicious `minter` could call `mint`, then immediately call `setMintingAllowedAfter` with a past timestamp (e.g., `block.timestamp - minimumTimeBetweenMints`), effectively resetting the cooldown period and allowing subsequent mints to occur without respecting the `minimumTimeBetweenMints` constraint. This bypasses a critical economic control.

**Recommendation:** Modify the `setMintingAllowedAfter` function to only allow setting a future timestamp that is greater than the current `mintingAllowedAfter` value, or remove the function entirely and rely solely on the `mint` function to update `mintingAllowedAfter` sequentially. Alternatively, ensure that `setMintingAllowedAfter` can only be called by a robust governance mechanism with appropriate time delays.


### `M-01` — Outdated Solidity Compiler Version  *(Severity: Medium · Status: Unresolved)*

The contract is compiled with Solidity version `^0.5.16`. Newer versions (e.g., `0.8.x`) include built-in overflow/underflow checks by default, reducing reliance on libraries like `SafeMath` and potentially offering gas optimizations and improved security features. Using an older compiler version might expose the contract to known compiler-level bugs or prevent it from benefiting from recent security enhancements.

**Recommendation:** Consider upgrading the contract to a more recent and stable Solidity compiler version (e.g., `0.8.x`). This would involve a thorough review and testing of the code to ensure compatibility and correct behavior with the new compiler.


### `L-01` — Non-Upgradeability of Contract  *(Severity: Low · Status: Unresolved)*

The contract is deployed as an immutable, non-upgradeable contract. While this simplifies the architecture and removes proxy-related risks, it means that any bugs discovered post-deployment cannot be fixed on-chain, nor can new features be added without deploying an entirely new contract and migrating all users and assets. This poses a long-term operational and maintenance challenge.

**Recommendation:** While a design choice, the project should be fully aware of the implications. For future contracts, consider using an upgradeable proxy pattern (e.g., UUPS) if the ability to fix bugs or add features post-deployment is desired. For this contract, ensure comprehensive testing and auditing to minimize the risk of immutable flaws.


### `I-01` — Use of Experimental ABIEncoderV2 Pragma  *(Severity: Informational · Status: Unresolved)*

The contract uses `pragma experimental ABIEncoderV2;`. While `ABIEncoderV2` has been stable since Solidity 0.6.0, its use in an older compiler version (`0.5.16`) where it was still marked as experimental could theoretically introduce unforeseen edge cases or vulnerabilities. Although widely adopted, relying on experimental features always carries a slight, albeit diminishing, risk.

**Recommendation:** If upgrading to a newer Solidity version (e.g., `0.8.x`), the `experimental` keyword for `ABIEncoderV2` can be removed as it is stable by default. For the current version, ensure thorough testing of all functions that rely on complex data types or nested arrays/structs to confirm correct ABI encoding/decoding behavior.

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
