## An Operating System-Level Certificate Pinning Solution

Cert Patrol is a great browser extension that fills the gap between the current tools available in Operating Systems and web browsers to ensure the integrity of TLS connections being made. Unfortunately, the web browser isn't the only application to make use of TLS within the Operating System.

If browsers are vulnerable to pinning attacks without this sort of protection, how can other applications, or Operating Systems themselves, rely on TLS and its related infrastructure without making themselves vulnerable to this sort of attack?

While many languages include the features to support Pinning functionality, not all applications go to the extent of implementing them.

For those applications and connections, currently a Cert Patrol-like userland application or kernel-space Daemon is the only way to protect against those types of attacks.
