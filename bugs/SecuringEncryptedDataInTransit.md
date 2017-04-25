## Securing User<->Server Interactions and Data Transmitted Over TLS in General.

#### Problem & Background
For as long as a I can remember, vulnerabilities in TLS's ability to hide server and end-user interactions have been well documented relating to the fact that page sizes of public websites are known, or easily discoverable, and by using that knowledge and observing the traffic (size, timing, etc.), anyone on the line can fairly easily retrace user<->site interactions.

To broaden or abstract that, there are scenarious under which other encrypted traffic may be subject to such eavesdropping (server<->server, server<->database, server to end-user applications, and on).

If enough information about the applications, servers, databases, schemas, or data that can be or is being transmitted is known, while there may not be sufficient leakage to give observers knowledge of precisely what is being communicated, enough information may be leaked out to allow adversaries to gain a sufficient picture of what is going on behind the scenes. On the other hand, and in the absolute worst case, if knobs (inputs) are exposed publicly and those adversaries are allowed to observe the traffic that results (the outputs), it may allow them to find weaknesses in, and eventually allow them to compromise the security of, the crypto infrastructure entirely.


#### Solution:
The best method of preventing this, and in general the best method of ensuring the security of encrypted data sent between parties by an observer with either of these abilities, is to allocate a constant bitrate between the server and client (or server<->server), to fill it with a constant stream of data--garbage or noise when critical TX/RX is not required, and to inject the actual, needed data into the stream in a seamless manner as needed.


#### Problem:
While that can be a viable option in some situations, unfortunately, in many others it is quite impractical (large-scale web applications, for example), as you, the server you're connected to, or neither the two of you can realistically allocate an entire fixed pipe to you and all of the other hundreds of thousands to millions of users connected to it. Nor would this necessarily be a desirable solution, as internet providers (at least in the USA) have recently begun transitioning to capping data-usage, similar to what cellular providers have always done.


#### Work-around:
A possible way of bypassing the fixed pipe Ideal Solution, assuming compression is not a concern (which at the time of initially writing this there were a few issues with it in TLS), utilizing it, and randomly changing the ratio or level, as well as randomizing the interval between the changing of the ratio. While observers would still be able to perform timing attacks, and estimate a users location on a site using an aggregate of other users browsing behavior, the precision would be thrown off as the second component (page size) would not be a factor, as there would be no way of predicting the arbitrary changes to the compression ratio used in the connection.

Additional methods of obfuscating ones activity on a site, aside from the fixed pipe solution that are probably not worth mentioning (as they would likely not be stomacheable by the masses) would be things like delayed TX/RX, in addition to randomizing the compression ratios.
