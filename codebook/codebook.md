# Codebook

## 1. Unit of analysis
One exploit incident against a cross-chain bridge or cross-chain messaging mechanism. Repeat attacks on the same bridge at different times are separate incidents. An *affected system* is the bridge or protocol named in the record; incidents on different components of the same protocol (e.g., Allbridge Core and the Allbridge CCTP router) count as one system.

## 2. Study period
1 January 2022 – 31 August 2026, based on the date each attack started.

## 3. Inclusion rule
The exploited component must be part of a cross-chain bridge or cross-chain messaging mechanism: deposit, lock and burn handling; relaying; proof and message verification; release and mint execution; or the bridge's own keys, governance, deployment, and operating infrastructure. Loss requires a documented transfer, withdrawal, unauthorised minting, or other realised economic impact affecting bridge-controlled assets or bridge users.

## 4. Exclusion rules
An incident is excluded if it is:
- an attack on a centralised exchange or custodial platform;
- an attack on a non-bridge component of a protocol that also offers bridging;
- an attack on an application that simply runs on several chains, or a theft whose funds were only moved across chains afterwards;
- an incident with no loss to the bridge or its users (including attempts prevented before any impact); or
- an incident that started before 1 January 2022.

## 5. Evidence rule and evidence levels
An incident is eligible if it has (i) an official incident report or post-mortem, (ii) at least two independent technical or reporting sources, or (iii) where no official root cause was disclosed, corroborated on-chain evidence with independent third-party reporting.

| Level | Definition |
|---|---|
| E1 | Official post-mortem (or official fix) plus at least one independent technical source |
| E2 | At least two independent technical or reporting sources |
| E3 | Official post-mortem or incident report only |
| E4 | On-chain tracing and third-party reports; root cause not officially disclosed (classification inferred) |

## 6. Loss measurement
**Gross bridge-specific loss**: the value of assets removed from the bridge, its liquidity, or bridge users, or minted without backing, as a direct consequence of the incident, in US dollars at the time of the attack. Recoveries, voluntary returns, and bounties are not subtracted. Excluded: unrelated losses at the same organisation, losses in other protocols caused later by stolen assets, market or price-impact estimates, and attempted but unrealised amounts. Where sources give a range, the lower bound is used (a predefined conservative rule). The `loss_basis` field records what each figure measures.

## 7. Counting rule
Each incident has exactly one primary attack pattern and one primary functional domain. Supporting methods (e.g., flash loans, phishing) do not create additional labels.

## 8. Coding procedure
1. Extract the attack mechanism from the evidence.
2. Identify the broken trust assumption.
3. List every pattern whose necessary condition is met (`attack_patterns.md`).
4. If more than one candidate remains, apply the boundary rules (`boundary_cases.md`).
5. Assign the primary pattern and domain and record the rationale.
6. Flag incidents that needed a boundary rule as boundary cases, with their alternative label.

## 9. Summary statistics
Quartiles use linear interpolation. The Gini coefficient is computed over the 48 incident-level gross losses (none is zero) as the mean absolute difference divided by twice the mean. Proportions are descriptive shares of the observed corpus; because the corpus is not a probability sample, no inferential confidence intervals or significance tests are reported.
