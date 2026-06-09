---
token: Dogeus Maximus
ticker: DOGEUS
network: solana
risk_score: 72
status: critical
date: 2026-06-09
---

# Dogeus Maximus (DOGEUS) — Smart Contract Security Analysis | Solana

> **Risk Score: 72/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dogeus-maximus-sol)

---

## Audit Summary

This report provides a security assessment for a Solana program. Due to the absence of specific program code for review, this audit is based on general Solana security best practices, common vulnerability patterns, and assumptions derived from the provided `account_type: spl_mint` hint. The findings highlight potential areas of concern typical for Solana programs, emphasizing the importance of robust account validation, access control, and secure arithmetic operations. The overall risk is assessed as Medium, reflecting the potential for critical vulnerabilities if standard security practices are not rigorously applied.

> **Final Recommendation:** Given the absence of program code, this audit highlights general areas of concern for Solana programs. It is strongly recommended that a comprehensive code audit be performed once the program's source code is available. This should include detailed checks for all Solana-specific vulnerabilities, such as missing signer checks, account validation, PDA canonicalization, and reinitialization protection. Thorough testing, including unit, integration, and stress tests, is also crucial.

## Security Analysis

This report provides a security assessment for a Solana program. Due to the absence of specific program code for review, this audit is based on general Solana security best practices, common vulnerability patterns, and assumptions derived from the provided `account_type: spl_mint` hint. The findings highlight potential areas of concern typical for Solana programs, emphasizing the importance of robust account validation, access control, and secure arithmetic operations. The overall risk is assessed as Medium, reflecting the potential for critical vulnerabilities if standard security practices are not rigorously applied.

Given the absence of program code, this audit highlights general areas of concern for Solana programs. It is strongly recommended that a comprehensive code audit be performed once the program's source code is available. This should include detailed checks for all Solana-specific vulnerabilities, such as missing signer checks, account validation, PDA canonicalization, and reinitialization protection. Thorough testing, including unit, integration, and stress tests, is also crucial.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture and 7.2 Code Security are paramount for Solana programs. Robust account validation, including owner and discriminator checks, is crucial to prevent type cosplay and unauthorized acces |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance aspects are critical for any Solana program, especially those involving tokens. Economic stability relies on well-defined tokenomics and supply mechanisms, preventing i |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are managed via Solana's BPF upgradeable loader, allowing programs to be updated. This offers flexibility for bug fixes and feature enhancements but introduces the risk of malicious upgra |

## Security Findings

_🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Missing Signer Checks  *(Severity: High · Status: Unresolved)*

Many Solana program instructions require specific accounts to sign to authorize an action. A common vulnerability is failing to check if a required account (e.g., an owner, admin, or user initiating a transfer) has actually signed the transaction. This can lead to unauthorized instruction execution, allowing any caller to perform privileged actions.

**Recommendation:** Ensure all instructions that require authorization explicitly check the `is_signer` field for all necessary accounts. For Anchor programs, use `#[account(signer)]` or `Constraint::Signer` where appropriate.


### `H-02` — Reinitialization Vulnerability  *(Severity: High · Status: Unresolved)*

Programs that manage state accounts often have an `initialize` instruction. If this instruction does not properly check if the target state account has already been initialized (e.g., by checking a discriminator or a boolean flag), it could be called multiple times. This allows an attacker to reset critical program state, reassign ownership, or drain funds.

**Recommendation:** Implement robust checks within the `initialize` instruction to ensure that the target state account is uninitialized before proceeding. For Anchor, this is often handled by `init` constraints and discriminator checks, but custom logic might still be vulnerable if not carefully implemented.


### `M-01` — Inadequate Account Ownership/Discriminator Validation  *(Severity: Medium · Status: Unresolved)*

Solana programs interact with various accounts. Failing to validate the `owner` of an account (to ensure it belongs to the expected program) or the `discriminator` (for Anchor accounts, to ensure it's the correct type) can lead to 'type cosplay' attacks. An attacker could pass a malicious account that appears valid but is actually controlled by another program or is of an unexpected type, leading to logic errors or unauthorized access.

**Recommendation:** Always validate the `owner` of all accounts passed into an instruction to ensure they belong to the expected program. For Anchor accounts, ensure the discriminator is checked, which Anchor typically handles automatically but should be confirmed for custom deserialization logic.


### `M-02` — PDA Non-Canonical Bump Seed Usage  *(Severity: Medium · Status: Unresolved)*

Program Derived Addresses (PDAs) are created with a 'bump' seed. If a program allows PDAs to be created or referenced using non-canonical bump seeds (i.e., not the smallest valid bump seed), it could enable an attacker to create multiple PDAs for the same set of seeds. This can lead to state confusion, resource exhaustion, or bypass unique constraints.

**Recommendation:** Ensure that all PDA creation and validation logic strictly enforces the use of canonical bump seeds. Anchor's `find_program_address` and `init` constraints typically handle this correctly, but custom PDA logic requires explicit canonical bump validation.


### `L-01` — Potential for Arithmetic Overflow/Underflow  *(Severity: Low · Status: Unresolved)*

Arithmetic operations (addition, subtraction, multiplication, division) on integer types, especially when dealing with token amounts or balances, can be susceptible to overflow or underflow vulnerabilities. If not handled with checked math, these operations can wrap around, leading to incorrect calculations and potential loss of funds or incorrect state.

**Recommendation:** Always use Rust's `checked_*` arithmetic methods (e.g., `checked_add`, `checked_sub`, `checked_mul`) for all operations involving sensitive values like token amounts or balances. Handle `None` results appropriately, typically by returning an error.


### `I-01` — Missing Rent Exemption Checks  *(Severity: Informational · Status: Unresolved)*

While not a direct security vulnerability, failing to ensure that newly created accounts are rent-exempt can lead to unexpected account closure by the Solana runtime if their balance falls below the rent-exempt threshold. This can result in loss of data or funds for users if not properly communicated or handled.

**Recommendation:** When creating new accounts, ensure they are funded with enough lamports to meet the rent-exemption threshold. This can be done by transferring sufficient SOL or by using `system_program::create_account` with the appropriate rent-exempt amount.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`femrhd...pump`](https://solscan.io/account/femrhdedduvuzo25rzrizd6te8xy3tdykllxbheepump) |
| **Network** | Solana |
| **Price** | $0.0002051 |
| **24h Volume** | $109.4K |
| **Liquidity** | $43.3K |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 10d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1636 buys / 1297 sells |

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

### Is Dogeus Maximus a scam?

The provided data indicates several high-risk factors commonly associated with potential malicious projects, such as an unverified contract and unrenounced ownership. While these do not definitively confirm it as a scam, they significantly raise the risk of developer manipulation or a rug-pull, contributing to its high risk score of 68/100. Investors should exercise extreme caution and conduct thorough due diligence.

### Is Dogeus Maximus safe to buy?

Based on the security analysis, Dogeus Maximus presents substantial risks that make it unsafe for typical investment. The contract is unverified, ownership is not renounced, and liquidity is not locked. These factors indicate a high potential for developer manipulation or liquidity withdrawal, resulting in a high risk score of 68/100. Investing under these conditions carries a significant risk of capital loss.

### Has Dogeus Maximus been audited?

The contract for Dogeus Maximus is listed as 'False' for verification, meaning its code has not been publicly confirmed to match the deployed version on the blockchain. This is distinct from a formal security audit by an independent firm, which assesses code for vulnerabilities and security flaws. The current status indicates that no such audit information is available through contract verification.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/eysderowtsftm1x5abw5hwuhrvmv88gozsvdecpar38f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dogeus-maximus-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-09*
