# Boundary Rules and Boundary Cases

## Boundary rules

| Patterns | Rule | Dataset examples |
|---|---|---|
| PF vs. LE | A flaw in the verification code itself that lets forged or invalid evidence pass is PF. A check left switched off by an initialisation or upgrade mistake, or a flaw outside verification, is LE. | PF: ZKSwap, Verus, CrossCurve. LE: Nomad, Ronin (2024), Messina |
| PF vs. EI | If the authenticity or validity of the evidence is incorrectly established, it is PF. If the evidence is authentic and correctly verified but does not describe a real deposit or burn, it is EI. | PF: Pike Finance, Wanchain. EI: Across, Coreum, warp.green |
| CS vs. PF | If stolen credentials directly approve the release or change the bridge contract, it is CS. If they only change who the verifier trusts and funds are then released through forged evidence, it is PF. | CS: ALEX Lab, Seedify. PF: GriffinAI, The Sandbox |
| CS vs. IH | Credentials taken directly from people, devices, storage, or key-management processes: CS. Credentials obtained by compromising the bridge's own build, deployment, or hosting systems: IH. | CS: Ronin (2022), Harmony, THORChain. IH: Force Bridge, Celer cBridge |
| PF vs. IH | If the compromised off-chain component itself performs verification, it is PF. | PF: Kelp DAO |
| ESM vs. LE | If the attack works only after first moving a trusted balance, price, or stake weight, it is ESM; if the coding flaw can be exploited directly, it is LE. | ESM: Allbridge (2023), Allbridge Core (2026), Shibarium. LE: Messina, Li.Fi |
| ESM vs. others | If a flash loan only funds the exploitation of another flaw, the incident takes that other pattern. | ESM: Allbridge (2023), Shibarium. EI: Allbridge CCTP router (2026) |

## Boundary cases

A boundary case is an incident for which two patterns each met a necessary condition during coding, so the primary pattern had to be chosen with a decision rule. These six cases are flagged in `data/incidents.csv` (`boundary_case = Yes`) and are switched between primary and alternative labels in the sensitivity analysis (all 2^6 = 64 combinations; `analysis/sensitivity_analysis.py`).

| Incident | Primary | Alternative | Reason for primary classification |
|---|---|---|---|
| Nomad (BR-041) | LE, FD-3 | PF, FD-3 | Messages passed verification without a valid proof, but the cause was a value set during an upgrade, not a flaw in the checking code. |
| GriffinAI (BR-021) | PF, FD-3 | CS, FD-5 | A stolen admin key was used only to change the trusted peer; tokens were then minted through forged evidence accepted by the verifier. |
| Kelp DAO (BR-014) | PF, FD-3 | IH, FD-5 | The compromised off-chain component performs verification, so the broken trust is in the verifier. |
| Force Bridge (BR-027) | IH, FD-5 | CS, FD-5 | Validator keys were obtained through malicious code inserted into a deployment image. |
| Shibarium Bridge (BR-024) | ESM, FD-4 | CS, FD-5 | The signing threshold was reached only because borrowed tokens temporarily inflated the attacker's stake. |
| Allbridge CCTP router (BR-003) | EI, FD-1 | PF, FD-3 | The flash loan only covered a funding shortfall; the message was genuinely attested, but the router credited a deposit without checking that funds had arrived. |
