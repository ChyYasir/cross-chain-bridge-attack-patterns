# Trust-Violation Attack Patterns

Each pattern is defined by the trust assumption the attacker breaks. Terms used consistently:
- **Attack pattern**: one of the six categories below.
- **Attack mechanism**: the concrete technical means used to carry out a pattern (e.g., a forged Merkle proof, a phished key).
- **Vulnerability**: the specific design or implementation weakness that makes the mechanism possible.
- **Functional domain**: where in the bridge the compromised trust boundary lies (see `functional_domains.md`).

| Group | Pattern | Trust broken | Necessary condition | Assigned to another pattern when |
|---|---|---|---|---|
| A – Verification and Contract Logic | Proof Forgery (PF) | The verifier accepts only valid evidence | The verifier accepts forged or invalid evidence (proof, signature, or message) that should fail its verification rule | The evidence is authentic but describes an event that did not happen (EI), or stolen keys approve the release directly (CS) |
| A – Verification and Contract Logic | Logic Exploitation (LE) | The remaining contract logic is correct | A coding flaw outside the verification check directly allows an unintended transfer | The flaw only works after the attacker first changes a trusted economic value (ESM) |
| B – Cross-Chain Information and Economic State | Event Injection (EI) | Deposit, burn, and event signals describe real actions | An authentic signal is accepted, but it represents a deposit or burn that did not happen or was not backed | The evidence itself is forged or invalid and passes only because the check is flawed (PF) |
| B – Cross-Chain Information and Economic State | Economic-State Manipulation (ESM) | Balances, prices, and stake weights reflect real economic conditions | The attacker changes an economically meaningful state value that the bridge trusts and later uses to approve or calculate a transfer | A flash loan only funds the exploitation of another flaw (that flaw's pattern) |
| C – Operational Trust Compromise | Credential Seizure (CS) | Only authorised parties hold and use the bridge's keys | Genuine credentials are used by an unauthorised party to approve actions | The credentials were obtained by compromising the bridge's own build, deployment, or hosting systems (IH) |
| C – Operational Trust Compromise | Infrastructure Hijacking (IH) | The bridge's hosting, DNS, and build systems are safe | The bridge's hosting, DNS, network routing, or build systems are compromised | Credentials are taken directly from people, devices, storage, or key-management processes (CS), or the compromised component itself performs verification (PF) |

## ESM classification test
An incident is ESM only if all four conditions hold: (i) the bridge uses a value that depends on pool, price, or stake state; (ii) the attacker changes that value through permitted actions (swaps, deposits, stake delegation), not through a coding flaw or stolen keys; (iii) the harmful transfer is calculated or approved using the changed value; and (iv) without the change, the same transfer would not have succeeded. ESM is a provisional pattern supported by three incidents.
