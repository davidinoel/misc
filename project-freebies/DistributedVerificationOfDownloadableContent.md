##Distributed Verification of Downloadable Content - DRAFT

####The problem this writeup attempts to address is that regardless of the adoption of TLS, both [broad and targeted attacks will always be a viable means of compromising systems][0], [and if viable, utilized][1]. Breaching networks, servers, download sites; finding or introducing implementation flaws in TLS, or weaknesses in its Cipher Suites and pulling off man-in-the-middle attacks; all of these can result in users downloading and processing these files, and becoming compromised as a result.

The essence of the problem is similar to the JavaScript A/V writeup:
#####There is a lot of data, and a lot of downloadable content that users have access to online. By accessing it, it can be downloaded and run; downloaded, stored, and later executed in any number of contexts; downloaded, parsed (a different way of saying "executed"); and the list goes on.

To differentiate this from the other (browser-based) projects I've written about here, I will clarify how and why this project is different.
- It is different because the goal is to focus exclusively on verifying downloadable content in general.
- Content is downloaded in a number of ways and a browser extension would only give the user some sense of security over their browser-based downloaded content.
- The purpose of this is that it be an application that the user runs on an Operating System-level.

The solution to this involves developing either a distributed, centralized, or hybrid model. Users downloading content would be able to verify it against the database of known files, and contribute hashes back to the database as well.

There are a number of ways the database could be obtained: built-in, acquired and updated upon peering, with continuted activity/connectivity to the network, or on a per request-basis to any of the servers hosting the file signatures.

In an ideal world any of these models would work equally well, but we do not live in such a place. Distributed models have their strengths and weaknesses, as do Centralized, and Hybrid models. The solution would involve extensive testing, auditing, fuzzing, and ultimately rely on the global security community and it recognizing the need for such an application.

Certainly, like everything in life, this is by no means without flaw. Even the idea of it. Ideally though it's a starting point for something bigger and better, such as a distributed network of proxies to download the content as well, and disposable test-beds to execute them in, and analyze them for malicious behavior.

[0]: https://medium.com/@hovm/the-law-of-software-bugs-47dcfd713f19 "Hovik's Law of Software Bugs"
[1]: https://marc.info/?l=freebsd-security&m=139715957600570&w=2 "David's Law of Vulnerabilites"
<html>
  <body>
    <text>
      &#91;0&#93;&nbsp;"Hovik's Law of Software Bugs":&nbsp;<a href="https://medium.com/@hovm/the-law-of-software-bugs-47dcfd713f19">https://medium.com/@hovm/the-law-of-software-bugs-47dcfd713f19<a/><br/>
      &#91;1&#93;&nbsp;"David's Law of Vulnerabilites":&nbsp;<a href="https://marc.info/?l=freebsd-security&m=139715957600570&w=2">https://marc.info/?l=freebsd-security&m=139715957600570&w=2<a/><br/>
    <text/>
   <body/>
<html/>
