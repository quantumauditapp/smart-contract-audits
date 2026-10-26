---
token: MOO DENG
ticker: MOODENG
network: ethereum
risk_score: 0
status: low
date: 2026-09-04
---

# MOO DENG (MOODENG) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/moo-deng-eth)

---

## Audit Summary

The `token` contract implements an ERC-20 standard with custom taxation, anti-bot, and anti-whale mechanisms. While it uses `SafeMath` for arithmetic safety, it exhibits critical centralization risks. The owner possesses extensive control over vital parameters, including the ability to halt trading or manipulate token economics, posing a severe risk to user funds and the token's utility. The anti-bot features, while intended for protection, are also centrally controlled and can be misused.

> **Final Recommendation:** It is strongly recommended to decentralize control over critical parameters to mitigate the significant centralization risks identified. Consider implementing a multi-signature wallet or a time-locked governance mechanism for sensitive functions like setting taxes, transaction limits, and managing bot lists. Thoroughly review the economic parameters, especially initial tax rates and anti-whale limits, to ensure they align with the project's long-term vision and do not inadvertently deter legitimate trading or create a 'honeypot' perception. If ownership is to be renounced, ensure all parameters are set to their final, desired state, and that the community understands the implications of an immutable contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes `SafeMath` to prevent integer overflows/underflows, which is a strong security practice (7.2 Code Security). However, the architecture grants the owner highly centralized… |
| **Governance / Economics** | 10/10 | Low | The economic model incorporates initial buy and sell taxes (21%) which can be reduced based on `_buyCount` thresholds (7.4 Economic). While this provides flexibility, the initial high taxes could… |
| **Upgrades** | 10/10 | Low | The contract is not designed with an upgrade mechanism (e.g., proxy pattern) (7.7 Upgrades). This means the contract's logic is immutable once deployed. While this eliminates risks associated with… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.4% (≈ permanent lock) |
| **LP Locked** | 99.4% — Null Address |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — High Initial Transaction Taxes  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is configured with high initial buy and sell taxes of 21% (`_initialBuyTax`, `_initialSellTax`). While these taxes are designed to reduce after certain `_buyCount` thresholds (`_reduceBuyTaxAt`, `_reduceSellTaxAt`), such high initial rates can deter early adoption, reduce trading volume, and create a perception of a 'honeypot' or an unsustainable economic model. This could negatively impact the token's liquidity and overall market health.

**Recommendation:** Consider lowering the initial tax rates to more standard levels (e.g., 5-10%) to encourage early trading and adoption. Clearly communicate the tax structure, including initial rates and reduction thresholds, to potential investors. Monitor the impact of tax rates on trading volume and adjust as necessary through a controlled governance process.


### `M-02` — Owner Privileges and Centralization Risk  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract owner possesses extensive control over critical token parameters, including the ability to set taxes (`setInitialBuyTax`, `setFinalSellTax`), transaction limits (`setMaxTxAmount`, `setMaxWalletSize`), manage bot lists (`addBot`, `delBot`), and enable/disable trading and swapping (`openTrading`, `setSwapEnabled`). This high degree of centralization allows the owner to manipulate the token's economy, halt trading by setting `_maxTxAmount` or `_maxWalletSize` to zero, or even redirect collected taxes by changing `_taxWallet`. A compromised owner key or a malicious owner could lead to a complete loss of user f

**Recommendation:** Implement a multi-signature wallet for ownership or transition to a decentralized governance model. For highly sensitive functions, consider adding a time-lock mechanism to allow users to react to pending changes. Clearly communicate the extent of owner privileges to the community.


### `M-03` — Anti-Bot/Anti-Whale Mechanisms with Centralized Control  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract includes anti-bot (`bots` mapping) and anti-whale (`_maxTxAmount`, `_maxWalletSize`, `sellCount` per block) mechanisms. While intended to protect against manipulation, these features are centrally controlled by the owner. The owner can arbitrarily add or remove addresses from the `bots` list, potentially blocking legitimate users. The `sellCount` limit per block can restrict users' ability to sell their desired amount, and can be circumvented by using multiple addresses. These mechanisms introduce subjective control and potential for abuse, impacting fair market operations and user liquidity.

**Recommendation:** Re-evaluate the necessity and implementation of these mechanisms. If retained, consider decentralizing control over the `bots` list through a community vote or a transparent, auditable process. Ensure that `_maxTxAmount` and `_maxWalletSize` are set to reasonable values that do not unduly restrict legitimate trading. Clearly document the behavior and limitations of these features.


### `L-01` — Front-running of `openTrading` Function  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `openTrading()` function, which enables transfers by setting `tradingOpen = true`, can be front-run. Malicious actors or bots can monitor the transaction pool for the `openTrading()` call and submit their own buy transactions with a higher gas price to be among the first to trade the token. This allows them to gain an unfair advantage in early trading, potentially buying at a lower price before wider market participation.

**Recommendation:** While this is a common characteristic of new token launches and not a direct vulnerability in the contract's logic, projects should be aware of this risk. Consider alternative launch mechanisms or clearly communicate the launch strategy to manage community expectations. No direct code change is typically required for this inherent market dynamic.


### `I-01` — Implications of Renouncing Ownership  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract includes a `renounceOwnership()` function, which allows the current owner to transfer ownership to the zero address. If ownership is renounced, all functions protected by the `onlyOwner` modifier become permanently inaccessible. This means that critical parameters such as tax rates, transaction limits, wallet limits, and the bot list can never be changed, and any potential issues or desired updates cannot be addressed. While this increases decentralization, it also removes any ability to adapt or mitigate future problems.

**Recommendation:** If the intention is to renounce ownership, ensure that all critical parameters are set to their final, desired state before renunciation. Clearly communicate the implications of renouncing ownership to the community, emphasizing that the contract will become immutable and unmanageable by any single entity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2856...bcad`](https://etherscan.io/address/0x28561b8a2360f463011c16b6cc0b0cbef8dbbcad) |
| **Network** | Ethereum |
| **Price** | $0.00000419 |
| **24h Volume** | $47.4K |
| **Liquidity** | $523.9K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 41.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 78 buys / 33 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x470dc172d6502ac930b59322ece5345dd456a03d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/moo-deng-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-04*
