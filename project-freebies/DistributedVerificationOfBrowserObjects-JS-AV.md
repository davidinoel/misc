##Distributed Verification Of Browser Objects: A JavaScript Antivirus - DRAFT

Here is the "JavaScript AntiVirus" document I've referred to in several others. I feel though, while JavaScript is a great place to start--a well known and common attack vector against browsers, that it might also be worth broadening it to "Browser Objects" in general. While the "Big Three" may be HTML, JavaScript, and CSS, as web standards, specifications, and languages develop, they add layer upon layer of complexity to the modern web browser. From this, bugs can arise in both places: the specification and the implementation of the browser. So naturally as the browsers evolve with these standards, new bugs are discovered.

I'd initially chosen and described this as a JS A/V because, as I said, it seems to be the primary attack vector against browsers (aside from Flash installations, phishing attacks, malicious downloads, and errors that those non-security-minded people might make), so I'll explain this using JS as the example, and then abstract it away to Browser Objects in general.

This may prevent an interesting addition to NoScript that would allow users to violate conventional wisdom of disallowing all scripts over HTTP, depending on how they are written.

The goals of this project are several. While it does share some similarities to the Distributed Verification of Remote Content write-up, in this case it could run as a browser extension. Primarily it would be to ensure that the JS received by the browser is secure; safe to run.

This could be as extreme taking a similar approach to how modern AntiVirus software builds intelligent detection systems on top of a combination of databases of known malicious code, signatures, similarities in behavior, distributed networks of sandboxes to fetch and load the pages and their JS and observing them for unexpected behavior, and manual code audits.

Or it could be as simple as a browser extension that hashes and distributes--either via a centralized, decentralized, or some combination of the two, network, the static JavaScript files that it receives. Pre-loaded with a database of JS files and hashes, it would be able to function out of the box--stand-alone--or upon peering or connecting to the (or one of the) main servers, it could fetch the database containing the URL's and hashes, use those to verify files as they came in, and also contribute hashes back to the network, and a signal to increment a counter when a file matches an expected hash.

Expanding to Browser Objects, one should never assume that any Browser Object is safe. While in most cases it's a safe bet that HTML alone is probably OK, there are other components of a webpage such as images, CSS, XML files, and on, whose parsers could very much be vulnerable to attack. Since scratching this down as a note in 2015 without writing it out in this way until now, there have been bugs uncovered in JavaScript engines, XML parsers, PNG exploits, and more.

The current trust model for moderately paranoid users who still want to browse the web seems to be that: if it comes over a secure connection and seems like a legitimate source it is likely trustworthy and can be executed, but if it comes over an insecure connection it should not be trusted any further than disabling all active content, and allowing the text and images to be parsed and displayed within your browser.

Due to the way CloudFlare et al. are configured, and how easily networks and servers are compromised, this couldn't be further from the truth.
