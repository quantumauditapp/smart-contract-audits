---
token: Lisk
ticker: LSK
network: base
risk_score: 63
status: medium
date: 2026-09-13
---

# Lisk (LSK) — Smart Contract Security Analysis | Base

> **Risk Score: 63/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lisk-base)

---

## Audit Summary

The L2LiskToken contract implements an ERC20 token with minting and burning capabilities controlled by a designated bridge address. While leveraging secure OpenZeppelin libraries, a critical vulnerability exists in the initialization process due to the use of `tx.origin` for access control, which could allow an attacker to hijack the bridge address. The token's economic security is highly dependent on the external bridge contract's integrity. Recommendations include addressing the `tx.origin` vulnerability and enhancing bridge security.

> **Final Recommendation:** It is imperative to immediately address the critical `tx.origin` vulnerability in the `initialize` function to prevent unauthorized control over the token's supply. Replacing `tx.origin` with `msg.sender` and ensuring secure initialization practices are paramount. Additionally, the security of the external `BRIDGE` contract must be rigorously maintained, as it represents the single point of failure for the token's economic integrity. 

Consider implementing an emergency pause mechanism to provide a failsafe in case of unforeseen vulnerabilities or bridge compromises. This would allow for temporary halting of critical operations, mitigating potential damage.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The `L2LiskToken` contract provides standard ERC20 functionality with `ERC20Permit` extensions, leveraging battle-tested OpenZeppelin libraries, which contributes to robust code security (7.2 Code… |
| **Governance / Economics** | 2/10 | High | The economic model of `L2LiskToken` is based on a centralized bridge mechanism, where the `BRIDGE` contract dictates the total supply through minting and burning (7.4 Economic). This design… |
| **Upgrades** | 3/10 | High | The `L2LiskToken` contract is not designed to be upgradeable (7.7 Upgrades). Key addresses like `REMOTE_TOKEN` are immutable, and the `BRIDGE` address is set once during initialization. This design… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low_

### `M-01` — `tx.origin` Usage for `initialize` Function Access Control  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function, which sets the critical `BRIDGE` address, uses `tx.origin` for access control (`require(msg.sender == initializer, ...)`). This is a known anti-pattern and makes the contract vulnerable to phishing attacks. If the `initializer` (an Externally Owned Account, EOA) interacts with a malicious contract, that malicious contract can then call `initialize` on `L2LiskToken` in the same transaction, effectively setting an arbitrary `BRIDGE` address. This would grant the attacker full control over the token's minting and burning capabilities, leading to potential economic collapse.

**Recommendation:** Replace `tx.origin` with `msg.sender` for access control in the `initialize` function. Ensure the `initializer` EOA is secure and only calls `initialize` directly. For critical administrative functions like initialization, consider using a multi-signature wallet to enhance security and decentralization.


### `M-02` — Centralized Control and Critical External Dependency on Bridge Security  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `L2LiskToken` contract's supply is entirely controlled by the `BRIDGE` address, which has exclusive permissions to mint and burn tokens. While this design is standard for L2 bridged tokens, it introduces a critical external dependency. The security and integrity of the token's supply are directly tied to the security of the external `BRIDGE` contract. A compromise of the `BRIDGE` contract would allow an attacker to arbitrarily mint or burn tokens, leading to a loss of the token's peg to its L1 counterpart and potential economic collapse.

**Recommendation:** Implement robust security measures for the `BRIDGE` contract, including thorough audits, multi-signature control, time-locks for critical operations, and continuous monitoring. Ensure the bridge's design minimizes attack surface and adheres to best security practices for cross-chain communication and asset custody.


### `L-01` — Lack of Emergency Pause Mechanism  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `L2LiskToken` contract lacks an emergency pause mechanism. In the event of a critical vulnerability in the bridge, an external dependency, or the token contract itself, there is no way to temporarily halt minting/burning or transfers to prevent further damage or mitigate ongoing exploits. This could lead to irreversible loss of funds or economic instability.

**Recommendation:** Consider implementing a pausable mechanism (e.g., using OpenZeppelin's `Pausable` contract) that can be triggered by a trusted role (e.g., a multi-signature wallet or a governance contract) to temporarily halt critical operations like minting and burning in emergencies. This provides a crucial failsafe for operational security (7.8 Operations).

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xac48...1a24`](https://basescan.org/address/0xac485391eb2d7d88253a7f1ef18c37f4242d1a24) |
| **Network** | Base |
| **Price** | $0.3882 |
| **24h Volume** | $1.40M |
| **Liquidity** | $340.0K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 86.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3836 buys / 5354 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x275be3a43b66516e532bcaa36ee453edd47614ea)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lisk-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*
