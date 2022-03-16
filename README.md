# Teleport-Merits-Demerits-over-ssh #

 Why we go with Teleport 
---

In general we use ssh-key to login to a node that is not in the local network.For this we need private keys of the server/vm and need to add it everytime while we accees the systems.Stolen private keys can bite you from a security standpoint for a long time because there is no auto-expiry time for keys, and they work until manually removed from the server.Key rotation can be a problem.Hard to implement on a large fleet of SSH servers

To avoid this difficulty we can use teleport which easily enforce MFA, RBAC, and SSO using identity-based short-lived certificates and leave SSH keys behind. This provides SSH access with minimal configuration




Certificate-centric design enables Teleport to deliver SSO, RBAC, per-session MFA, and other modern security best practices for SSH access.

Certificate-based protocol negotiation shrinks the network attack surface area of all Linux servers to a single TCP/IP port and reduces operational overhead.

Move away from root accounts with just-in-time SSH privilege escalation for administrative tasks. Access requests can be approved via Slack or other supported plugins.

Avoid human errors using Teleport FIPS mode which rejects configuration options unless they are compliant with FIPS 140-2, also known as the Federal Information Processing Standard.
Unlike OpenSSH, the Teleport SSH daemon periodically (every 5 seconds by default) sends a service ping to a Teleport CA. This allows users to see what nodes are available.This is also used to submit the information about node state to the cluster which can then be used for accessing nodes by dynamic labels.

Implement moderated sessions, enforce concurrent session restrictions, proactive session termination and identity locking across your entire infrastructure footprint.

With a real-time inventory of all your Linux servers in the cloud, on-prem, or edge, resource discovery and maintenance are easy.

See all live interactive SSH sessions across your entire fleet. Easily join another user’s session for pair programming or debugging.
Automate access provisioning and access request approvals using your favorite programming language.

Every interactive session is recorded for future replay and can be analyzed by other tools for behavior anomalies.

Consolidate all security events across all environments in a single source of truth and export them into a SIEM solution of your choice.

Teleport offers enhanced session recordings based on BPF events so every system call during an SSH session can be audited.
Teleport supports reverse SSH tunnels out of the box (connect to nodes behind a firewall)

 Web UI support copy and paste;Teleport employs tmux-like "prefix" mode.



security---Capture sessions and manage certificates for existing OpenSSH fleet.Replace static keys and passwords with short-lived certificates.
            Gather structured events and session recording/replay for ssh, kubectl and desktop interactions.Enforce two-factor auth with WebAuthn or TOTP.

developers--Collaborate through session sharing.Discover servers and clusters with dynamic node labels.Connect to computing resources located behind firewalls or   
             without static IPs.



Demerits
--------------


1)Teleport software must be running on every server to be managed by Teleport access.

2)Complex setup: in addition to the Teleport software on each server, a Teleport Proxy and TeleportAuth server must also be built and maintained for each cluster.

3)CLI-only client scares off non-engineers.

4)User credentials are assigned across a full cluster rather than server-by-server.

5)Backend configuration required to store audit logs (AWS S3 / DynamoDB, required by teleport to store session logs).

6)Teleport agent audit logs are only accessible through the UI or backend storage.

7)Complex pricing model.

8)Teleport community edition supports only uses local users or github for identity-based authentication.only community support is available.No RBAC,No SSO   integration,No paid support available










