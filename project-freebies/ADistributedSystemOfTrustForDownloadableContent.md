##A Distributed System of Trust For Downloadable Content - DRAFT

####The problem this writeup attempts to address is that regardless of the adoption of TLS, both [broad and targeted attacks will always be a viable means of compromising systems][0], [and if viable, utilized][1]. Breaching networks, servers, download sites; finding or introducing implementation flaws in TLS, or weaknesses in its Cipher Suites and pulling off man-in-the-middle attacks; all of these can result in users downloading and processing these files, and becoming compromised as a result.

There may be some overlaps here with the JavaScript Antivirus I describe in another document, and the essence of the problem really is the same:
#####There is a lot of data, and a lot of content that users have access to online. By accessing it, it can be downloaded and stored; downloaded, stored and executed in any number of contexts; downloaded, parsed (a different way of saying "executed"), and used; and the list goes on.

I should try to define how this project is different from the JavaScript A/V. The goal of this project is to focus exclusively on downloadable content that . Another advantage is that excluding Browser Objects would allow this to be run at an OS-level

The solution to this could involve developing perhaps a distributed, or perhaps a number of centralized systems. In an ideal world either solution would work equally well, but we do not live in such a world. Distributed models have their strengths and weaknesses, as do Centralized, and Distributed-Centralized models. The solution would involve users downloading the online content, and then verifying it against a database of known files. This database could be built-in, acquired and updated upon peering, and continuted activity on the network, or per request to any of the servers hosting the file signatures.


One could say: perhaps this model may only thwart targeted attacks against individuals, as users running this against downloads from a compromised server passing out signed binaries of an Open Source project would all wind up with the same hash, it would be confirmed by the projects server, and only people who were very careful to install this into a test-bed and watch it for any unexpected behavior, or if it were to build reproducably, those building it would also be able to raise an alarm... after the fact (the worst time to raise the alarm, depending on the attacker).

On the other hand, if an attacker compromised a website with a known and hashed download, modified it, and future users downloaded it as well, it would immediately raise a red flag, and give the user reason to investigate, check alternative channels for hash information, and save many from infecting themselves from, what today can be, for non-experienced Computer Engineers and Systems Developers, the end of a computer's life.

[0]: https://medium.com/@hovm/the-law-of-software-bugs-47dcfd713f19 "Hovik's Law of Software Bugs"
[1]: https://marc.info/?l=freebsd-security&m=139715957600570&w=2 "David's Law of Vulnerabilites"
