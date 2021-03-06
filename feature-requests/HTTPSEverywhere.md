## HTTPSEverywhere

1.) Not All TLS Protocols and Cipher Suites Are the Same

As research on old standards is performed and flaws are uncovered, they are deprecated, and new Protocols and Suites are recommended. Unfortunately this information does not spread as quickly as it would in an ideal world, and servers are left exposed on the internet running outdated and dangerous versions, supporting insecure protocols and Cipher Suites.

For these reasons, useful features to include in HTTPSEverywhere would be:
- To make visible to users information about the TLS connection (protocol, cipher suite, and optionally verion) that they're initiating a connection with.
- A "Simplified" mode for less savvy users who may not have set restrictions on the protocols and cipher suites through which the browser is allowed to connect, or may not know how to make those changes. For these users it would be helpful to have a few options within the extension that would allow them to select the level of TLS security that they desire. This ties in to the following point, and the color-coding interface may be something that could be utilized, along with an explanation as to what that color-coding system means, in plain language, in terms of overall risk (transport, server, and/or end-user compromise).
- Along with this "Simlified" mode, a grading or a color-coding system such as Red, Yellow, and Green may also be useful to allow users to know which protocols are considered reasonably safe and which are not.

1a.) No TLS Implementation is Without Flaw

Even the "latest and [thought to be] greatest" Protocols, Cipher Suites, and Implementations of TLS aren't always safe to use. The standard can very easily be implemented incorrectly, and history--with a long list of CVE's and Security Advisories--shows this to be true.

For this reason, another great feature to have would be to incorporate the latest tools released by security researchers to test and verify TLS implementations for [correctness][0], so that users aren't [given an entirely false sense of security as to whether they can be compromised, or MITM'd when making a connection][1].

[0]: https://gcm.tlsfun.de/ "Nonce reuse was a recent disclosed issue at the time this was originally written"
[1]: https://www.google.com/ "Vulnerabilities to compromise servers via flaws in TLS implementations aren't unheard of. CloudFlare et al. allow servers to send unencrypted traffic to them, whereupon they then encrypt it, relay it on to the end-user, leaving a number of hops open for compromise, and the end-user's none the wiser, and on."

* For both of these, a database of white-listed websites would work, but it would require constant and distributed scanning, and would still not prevent targeted attacks by compromised servers, or attacks on the database itself. For the sake of end-user security, incorporating the tools to verify the connections into their browsers is the ideal solution. *

<html>
  <body>
    <text>
      &#91;0&#93;&nbsp;"Nonce reuse was a recent disclosed issue at the time this was originally written"&nbsp;-&nbsp;&#91;<a href="https://gcm.tlsfun.de/">https://gcm.tlsfun.de/<a/>&#93;<br/>
      &#91;1&#93;&nbsp;"Vulnerabilities to compromise servers via flaws in TLS implementations aren't unheard of. CloudFlare et al. allow servers to send unencrypted traffic to them, whereupon they then encrypt it, relay it on to the end-user, leaving a number of hops open for compromise, and the end-user's none the wiser, and on."&nbsp;-&nbsp;&#91;<a href="https://www.google.com/">https://www.google.com/<a/>&#93;<br/>
    <text/>
   <body/>
<html/>
