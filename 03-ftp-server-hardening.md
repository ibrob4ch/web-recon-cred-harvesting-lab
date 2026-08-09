# Part 3 — FTP Server Setup on Windows Server 2016

Before the credential cracking exercise in Part 4 could take place, a target FTP service needed to be built — and hardened realistically enough to be a meaningful cracking target rather than a trivially open service.

## Build Steps

1. **Installed the FTP Server role** on Windows Server 2016 via Server Manager.
2. **Created an FTP site**, bound to the server, serving as the target service for the exercise.
3. **Created a dedicated Windows user group** for FTP access — separating FTP-permitted accounts from general server accounts, rather than granting FTP access broadly.

## Hardening Measures Applied

### User Isolation

Configured **FTP User Isolation** so that each authenticated user is restricted to their own home directory upon connection, with no visibility into or access to other users' directories. This is a standard FTP hardening control — without it, any authenticated user (even a low-privilege one) can potentially browse or access files belonging to every other FTP user on the same server.

### Virtual Directories and Permissions

Added a virtual directory to the FTP site and explicitly configured its permission set, rather than relying on default inherited permissions — ensuring access was scoped to only what the exercise required.

### Firewall Configuration

Configured **Windows Firewall with Advanced Security** with the three inbound rules required for external FTP connectivity (control channel plus the passive/active data channel rules FTP requires beyond a single port). Without correctly scoped firewall rules, FTP's use of dynamic data ports beyond the standard control port (21) is a common source of "it doesn't work" — getting this right was itself a useful piece of the exercise, distinct from the security-hardening steps above.

## Validation

Connected to the FTP server successfully from two separate clients — the Windows command-line FTP client and a web browser — confirming the service was correctly reachable and the firewall rules were functioning as intended before moving to the cracking exercise.

## Why this matters as a companion to Part 4

Building the target service myself (rather than attacking a pre-existing black-box target) meant fully understanding what "successful" looks like from the defender's side — user isolation, permission scoping, and firewall configuration — before turning around and attacking that same service in [`04-credential-cracking-dictionary-attack.md`](./04-credential-cracking-dictionary-attack.md). Seeing both sides of the same service reinforces why credential-based attacks succeed in the first place: none of the hardening steps above (isolation, permissions, firewall rules) actually stop a weak-password dictionary attack — that gap is exactly what Part 4 demonstrates.
