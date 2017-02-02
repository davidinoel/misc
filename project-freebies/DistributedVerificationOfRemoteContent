DistributedVerificationOfRemoteContent - DRAFT
==============================================

A Distributed System of Trust For Online Content:

There may be some overlaps here with the JavaScript Antivirus I describe in another document, and the essence of the problem really is the same: there is a lot of data, and a lot of content that users have access to online. By accessing it, it can be downloaded and stored, downloaded, parsed, and used... or even executed.

I should try to define how this project is different from the JavaScript A/V, and while it's tempting to make a blanket statement that this should cover all non-JS objects (and while that would be a great project and a great end-goal to have), maybe narrowing this a bit would be good, and focusing exclusively on content on public websites that users are able to download (as in: save to disk, open in a viewer of some sort, or execute).

The problem here is that with or without widespread adoption of TLS, regardless, either broad or targeted attacks can be performed by breaching servers, download sites, or pulling off man-in-the-middle attacks, and systems that download and process these files can become compromised as a result.

The solution to this could involve developing perhaps a distributed, or perhaps a number of centralized systems. In an ideal world either solution would work equally well, but we do not live in such a world. Distributed models have their strengths and weaknesses, as do Centralized, and Distributed-Centralized models. The solution would involve users downloading the online content, and then verifying it against a database of known files. This database could be built-in, acquired and updated upon peering, and continuted activity on the network, or per request to any of the servers hosting the file signatures.


One could say: perhaps this model may only thwart targeted attacks against individuals, as users running this against downloads from a compromised server passing out signed binaries of an Open Source project would all wind up with the same hash, it would be confirmed by the projects server, and only people who were very careful to install this into a test-bed and watch it for any unexpected behavior, or if it were to build reproducably, those building it would also be able to raise an alarm... after the fact (the worst time to raise the alarm, depending on the attacker).

On the other hand, if an attacker compromised a website with a known and hashed download, modified it, and future users downloaded it as well, it would immediately raise a red flag, and give the user reason to investigate, check alternative channels for hash information, and save many from infecting themselves from, what today can be, for non-experienced Computer Engineers and Systems Developers, the end of a computer's life.
