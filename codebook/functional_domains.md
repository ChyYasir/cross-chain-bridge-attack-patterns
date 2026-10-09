# Functional Domains

FD-1 to FD-4 form the transfer-processing path. FD-5 is a cross-cutting governance and operational control plane, not a step in the path. The domain is assigned to the component or trust boundary directly compromised, not to the downstream operation enabled by the compromise; credential and infrastructure compromises are therefore FD-5 even when the fraudulent action is later processed in FD-3 or FD-4.

| Domain | Role | Coding question |
|---|---|---|
| FD-1 Deposit | Lock or burn assets and record the transfer | Was the source-side record of a deposit, lock, or burn manipulated? |
| FD-2 Relay | Produce and transmit evidence of the transfer | Was the transmission or reading of a cross-chain event or message manipulated? |
| FD-3 Verification | Decide whether the evidence is acceptable | Was the authenticity or validity of a message or proof incorrectly established? |
| FD-4 Execution | Mint or release assets on the destination chain | Was an accepted instruction executed incorrectly, or based on manipulated state? |
| FD-5 Governance & Operations | Manage and update the bridge over time | Were keys, validators, administrative rights, deployment, or infrastructure compromised? |
