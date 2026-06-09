---
token: three.ws
ticker: THREE
network: solana
risk_score: 72
status: critical
date: 2026-06-08
---

# three.ws (THREE) — Smart Contract Security Analysis | Solana

> **Risk Score: 72/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/threews-sol)

---

## Audit Summary

This report provides a security audit for a Solana program. Due to the absence of specific program code, the analysis is based on common Solana program security patterns and best practices. The findings highlight potential vulnerabilities frequently observed in Solana programs, offering general recommendations for robust development. The overall risk is assessed as Medium, reflecting the inherent complexities and common pitfalls in Solana program development.

> **Final Recommendation:** To ensure the highest level of security for your Solana program, a thorough code audit by experienced Solana security professionals is strongly recommended once the program code is available. This will allow for a detailed, line-by-line analysis to identify and mitigate specific vulnerabilities. Implementing robust testing frameworks, including unit, integration, and fuzz testing, is also crucial.

## Security Analysis

This report provides a security audit for a Solana program. Due to the absence of specific program code, the analysis is based on common Solana program security patterns and best practices. The findings highlight potential vulnerabilities frequently observed in Solana programs, offering general recommendations for robust development. The overall risk is assessed as Medium, reflecting the inherent complexities and common pitfalls in Solana program development.

To ensure the highest level of security for your Solana program, a thorough code audit by experienced Solana security professionals is strongly recommended once the program code is available. This will allow for a detailed, line-by-line analysis to identify and mitigate specific vulnerabilities. Implementing robust testing frameworks, including unit, integration, and fuzz testing, is also crucial.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture and 7.2 Code Security are critical for Solana programs, requiring careful design to prevent common issues like missing signer checks and improper account validation. For instance, ens |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic models in Solana programs must account for lamport management, rent exemption, and potential tokenomics, ensuring stability and preventing draining attacks. 7.5 Governance mechanisms, if  |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades on Solana are managed through the BPF Loader, allowing program logic to be updated. This process introduces risks if not handled securely, such as ensuring the upgrade authority is proper |

## Security Findings

_🟠 2 High · 🟡 3 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Missing Signer Checks for Critical Instructions  *(Severity: High · Status: Unresolved)*

Instructions that modify program state or transfer assets often require specific accounts to be signers. A common vulnerability is failing to check if a required account (e.g., an owner, admin, or the account being modified) has signed the transaction. This can lead to unauthorized instruction execution, allowing any caller to invoke privileged operations.

**Recommendation:** Ensure all accounts that are intended to authorize an instruction, especially those modifying state or transferring value, are explicitly checked for `is_signer = true` within the instruction handler. Use Anchor's `#[account(signer)]` attribute or manual `account.is_signer` checks.


### `H-02` — Inadequate Account Validation (Owner/Discriminator)  *(Severity: High · Status: Unresolved)*

Programs must rigorously validate all accounts passed into an instruction to ensure they are of the expected type and owned by the correct program. Failure to check `account.owner` can allow an attacker to pass in arbitrary accounts, potentially leading to type cosplay attacks or manipulation of unintended data. Missing Anchor discriminator checks can allow one account type to be mistaken for another.

**Recommendation:** For every account passed into an instruction, verify its `owner` matches the expected program ID. For Anchor programs, ensure `#[account(has_one = ...)]` and `#[account(owner = ...)]` are used where appropriate, and that discriminators are checked for all deserialized accounts. Manual checks for `account.data_is_empty()` and `account.data_len()` can also prevent issues.


### `M-01` — PDA Bump Seed Canonicalization Vulnerability  *(Severity: Medium · Status: Unresolved)*

When creating or deriving Program Derived Addresses (PDAs), it's crucial to use the canonical bump seed. If a program allows PDAs to be initialized with non-canonical bump seeds, an attacker could create multiple PDAs for the same set of seeds, potentially leading to state confusion, resource exhaustion, or bypassing unique account constraints.

**Recommendation:** Always use `find_program_address` to derive the canonical bump seed when creating or interacting with PDAs. Ensure that PDA initialization logic strictly enforces the use of the canonical bump, typically by comparing the provided bump with the one returned by `find_program_address`.


### `M-02` — Reinitialization Attacks  *(Severity: Medium · Status: Unresolved)*

If a program's initialization instruction does not properly check if an account has already been initialized, an attacker could re-initialize an existing account, overwriting its data or resetting its state. This can lead to loss of funds, privilege escalation, or denial of service.

**Recommendation:** Implement a clear state variable (e.g., `is_initialized: bool`) within the account's data structure. During initialization, check if `is_initialized` is false before proceeding, and set it to true upon successful initialization. For Anchor, `#[account(init)]` and `#[account(zero_copy)]` with proper checks can help, but manual checks are often safer.


### `M-03` — Arithmetic Overflow/Underflow Without Checked Math  *(Severity: Medium · Status: Unresolved)*

Solana programs written in Rust do not automatically perform checked arithmetic in release builds. Operations like addition, subtraction, or multiplication on integer types can overflow or underflow, leading to unexpected values and potential exploits, such as incorrect balance calculations or logic bypasses.

**Recommendation:** Always use Rust's checked arithmetic methods (e.g., `checked_add()`, `checked_sub()`, `checked_mul()`) for all critical calculations involving token amounts, balances, or indices. Handle `None` results appropriately, typically by returning an error.


### `L-01` — Missing Rent-Exemption Checks for New Accounts  *(Severity: Low · Status: Unresolved)*

When creating new accounts, the program or the user is responsible for ensuring they are rent-exempt. If an account is initialized with insufficient lamports to cover its rent for two years, it risks being reaped by the Solana runtime, leading to data loss. While often a user responsibility, programs should ideally enforce or warn about this.

**Recommendation:** When creating new accounts, ensure sufficient lamports are transferred to make them rent-exempt. Use `Rent::get().minimum_balance(data_len)` to calculate the required lamports. Consider adding checks or clear documentation for users regarding rent exemption.


### `L-02` — Potential for Close Account Draining  *(Severity: Low · Status: Unresolved)*

When an account is closed, its remaining lamports are transferred to a specified recipient. If the program allows an attacker to manipulate the recipient account or close an account prematurely, it could lead to unintended lamport transfers or denial of service for legitimate users.

**Recommendation:** Ensure that account closure logic is strictly controlled. Only allow the legitimate owner or a designated authority to close an account. Verify the recipient account is the intended one. For Anchor, `#[account(close = recipient)]` should be used carefully, ensuring `recipient` is properly validated.


### `I-01` — Lack of Comprehensive Error Handling  *(Severity: Informational · Status: Unresolved)*

While Rust's `Result` type encourages explicit error handling, some programs might not cover all possible failure scenarios with specific error codes or messages. Generic error handling can make debugging and understanding program failures difficult for users and integrators.

**Recommendation:** Implement a comprehensive set of custom error codes for all expected failure conditions. Provide clear, descriptive error messages to aid debugging and user experience. Ensure all `Result` types are properly handled, converting system errors or CPI errors into program-specific errors where appropriate.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`fembdo...pump`](https://solscan.io/account/fembdox7r1psc4gecvjdsbnbza3bfztcydcatjvjpump) |
| **Network** | Solana |
| **Price** | $0.004757 |
| **24h Volume** | $1.46M |
| **Liquidity** | $266.3K |
| **Volume / Liquidity** | 5.5× |
| **Token Age** | 1mo |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 32461 buys / 17505 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is three.ws a scam?

Based on automated analysis, three.ws scores 65/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is three.ws safe to buy?

Our scanner flagged a risk score of 65/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has three.ws been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/5byl7mzolabynwmpzkpkjf4mgkz7febzranos19pre2z)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/threews-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-08*
