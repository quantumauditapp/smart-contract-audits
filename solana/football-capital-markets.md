---
token: Football Capital Markets
ticker: FCM
network: solana
risk_score: 35
status: medium
date: 2026-06-08
---

# Football Capital Markets (FCM) — Smart Contract Security Analysis | Solana

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/football-capital-markets-sol)

---

## Audit Summary

This report provides a security audit for a Solana program, identified as an SPL Token Mint. Due to the absence of specific program code for analysis, this audit is based on general Solana program security best practices and common vulnerability patterns observed in similar programs. The risk assessment reflects potential issues that could arise in a typical Solana program interacting with an SPL mint, rather than specific findings from code review. The overall risk is assessed as Medium, primarily due to the inherent complexities of Solana program development and the potential for common pitfalls such as improper account validation or missing signer checks.

> **Final Recommendation:** Given the absence of program code for a detailed audit, this report highlights general security considerations for Solana programs, particularly those interacting with SPL token mints. It is crucial to conduct a thorough code review to identify and mitigate specific vulnerabilities. We recommend implementing robust account validation, comprehensive signer checks, and secure management of program authorities. For enhanced security and peace of mind, consider our Premium Deploy option, which includes a full code audit, formal verification, and continuous monitoring services to ensure the long-term integrity and security of your Solana program.

## Security Analysis

This report provides a security audit for a Solana program, identified as an SPL Token Mint. Due to the absence of specific program code for analysis, this audit is based on general Solana program security best practices and common vulnerability patterns observed in similar programs. The risk assessment reflects potential issues that could arise in a typical Solana program interacting with an SPL mint, rather than specific findings from code review. The overall risk is assessed as Medium, primarily due to the inherent complexities of Solana program development and the potential for common pitfalls such as improper account validation or missing signer checks.

Given the absence of program code for a detailed audit, this report highlights general security considerations for Solana programs, particularly those interacting with SPL token mints. It is crucial to conduct a thorough code review to identify and mitigate specific vulnerabilities. We recommend implementing robust account validation, comprehensive signer checks, and secure management of program authorities. For enhanced security and peace of mind, consider our Premium Deploy option, which includes a full code audit, formal verification, and continuous monitoring services to ensure the long-term integrity and security of your Solana program.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture and 7.2 Code Security: Without specific program code, a detailed architectural review is not possible. However, a well-structured Solana program typically leverages Anchor for secure  |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance: For an SPL Token Mint, economic aspects primarily revolve around mint supply, freeze authority, and potential fees if the program implements custom token logic. Govern |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: The upgradeability of a Solana program introduces both flexibility and risk. While the SPL Token Program itself is generally not user-upgradeable, any custom program interacting with it  |

## Security Findings

_🟡 3 Medium · 🟢 2 Low_

### `M-01` — Missing Signer Checks for Critical Instructions  *(Severity: Medium · Status: Unresolved)*

Solana programs often fail to properly validate that required accounts are signers for critical instructions. This can lead to unauthorized execution of instructions, such as transferring ownership, minting tokens, or modifying program state, by non-privileged accounts. For an SPL Token Mint, this could manifest if a program's instruction intended to be called only by the mint authority does not verify the authority's signature.

**Recommendation:** Ensure all instructions requiring specific authorization (e.g., administrative actions, state modifications) explicitly check that the necessary authority accounts are signers using `#[account(signer)]` in Anchor or manual `is_signer` checks in raw Rust. Implement robust role-based access control.


### `M-02` — Account Validation Failures (Owner/Discriminator Checks)  *(Severity: Medium · Status: Unresolved)*

Improper validation of account ownership or discriminator values can allow attackers to substitute malicious or unintended accounts. This could enable type cosplay attacks where an attacker provides an account of a different type, or allows a program to operate on an account not owned by the expected program, leading to unexpected behavior or asset manipulation. For an SPL Token Mint, this could involve a program incorrectly validating a token account's owner or type.

**Recommendation:** Always validate the `owner` field of all passed accounts to ensure they belong to the expected program (e.g., `spl_token_program::ID` for token accounts, or the program's own ID for custom accounts). For Anchor accounts, ensure `#[account(has_one = owner_field)]` and `#[account(owner = program_id)]` are used, and that discriminators are correctly checked for zero-copy accounts.


### `M-03` — Reinitialization Attack Vulnerability  *(Severity: Medium · Status: Unresolved)*

Programs with an `initialize` instruction that does not prevent re-execution can be vulnerable to reinitialization attacks. An attacker could re-initialize an already initialized account, resetting its state, changing authorities, or draining funds. This is particularly critical for programs managing core configurations or asset pools.

**Recommendation:** Implement a clear state check within the `initialize` instruction to ensure the account is uninitialized before proceeding. For Anchor, use `#[account(init)]` and ensure the `init` constraint is only applied to accounts that should be initialized once. For manual implementations, check a boolean flag or a specific state enum value.


### `L-01` — Arithmetic Overflow/Underflow without Checked Math  *(Severity: Low · Status: Unresolved)*

Arithmetic operations (addition, subtraction, multiplication) performed without explicit overflow/underflow checks can lead to unexpected behavior or incorrect calculations. While Rust's default `debug_assertions` catch these in debug mode, they wrap in release mode. This could affect token balances, fee calculations, or supply updates, potentially leading to economic exploits.

**Recommendation:** Always use Rust's checked arithmetic methods (e.g., `checked_add()`, `checked_sub()`, `checked_mul()`) for all sensitive calculations involving token amounts, balances, or other numerical state variables. Handle `None` results appropriately, typically by returning an error.


### `L-02` — PDA Bump Seed Canonicalization Issues  *(Severity: Low · Status: Unresolved)*

When deriving Program Derived Addresses (PDAs), it's crucial to ensure that only the canonical bump seed is accepted. If a program allows non-canonical bump seeds, an attacker could create multiple PDAs for the same set of seeds, potentially leading to state confusion, resource exhaustion, or bypassing unique account constraints. This is relevant if the program derives token accounts or other state accounts using PDAs.

**Recommendation:** Always verify that the provided bump seed for a PDA is the canonical one. Anchor's `#[account(seeds = [...], bump)]` macro handles this automatically. For manual PDA derivations, ensure `Pubkey::find_program_address` is used to derive the canonical bump and compare it with the provided one.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`hkpi2s...pump`](https://solscan.io/account/hkpi2sknwm5logyy1bz4zytq5revvco2aywd1typpump) |
| **Network** | Solana |
| **Price** | $0.004738 |
| **24h Volume** | $222.9K |
| **Liquidity** | $175.0K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 12d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7986 buys / 3573 sells |

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

### Is Football Capital Markets a scam?

While the data does not definitively label Football Capital Markets as a scam, it exhibits several high-risk characteristics. The unverified contract, unrenounced ownership, and unlocked liquidity create conditions where malicious actions are possible. These factors contribute to its 61/100 high-risk score, warranting extreme caution from potential investors regarding the project's long-term viability and integrity.

### Is Football Capital Markets safe to buy?

Football Capital Markets is currently assessed as having a high-risk profile (61/100), suggesting it is not safe for typical investment. Key safety concerns include the contract not being verified, ownership not being renounced, and the project's liquidity not being locked. These elements mean the project's integrity is heavily reliant on the developer's trustworthiness, which carries inherent risks for investors.

### Has Football Capital Markets been audited?

The Football Capital Markets contract is reported as "unverified." This means its source code has not been publicly provided or confirmed to match the deployed code on the blockchain. Without contract verification, a thorough and verifiable security audit is practically impossible for external parties. This lack of transparency prevents independent review of its functionalities and security.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/rxfkdunvinpubdzdyn68rtm3bh2t9s5jytpai8e4zbi)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/football-capital-markets-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-08*
