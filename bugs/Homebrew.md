## Homebrew - First Published: 20170220

#### INTRO:
Based on how long it's taken for the bug report describing the issue of adding the "--require-sha" flag to ~/.&#91;shell&#93;&#95;profile's HOMEBREW_CASK_FLAGS, it breaking of the `brew cask search` command to be filed, and its recognition among the tech community, it's surprising that this and other similar conversations didn't come up far sooner.

- Roughly 20% of Homebrew Cask Formula's currently contain "sha256 :no_check", meaning that not only do they lack the basc layer of security most would expect from a package manager by not allowing Caskroom to verify their sha256 signatures, but that if end-users were to set the --require-sha flag, 20% of the software packages via Caskroom would be unavailable to them because the signatures were not provided by the maintainers in the Formula.  
<
% cd /usr/local/Homebrew/Library/Taps/caskroom  
% find . |grep "\.rb" | wc -l  
    3779  
% grep -r "sha256 :no_check" | wc -l  
    761  
761/3779 ~= 20%  
>
- There's a valid conversation that needs to take place about the way hashes are obtained, and their reliability. If a download site is using HTTP, and an attacker is sitting a hop or two in front of the download site, it's trivial for both the download file and the hash itself to be compromised, with neither the package maintainer nor the average Homebrew user being any the wiser. In this MITM'd scenario, the maintainer would download the compromised package and corresponding hash, and then update the Formula with the corresponding sum and link, and push it live, allowing millions of Homebrew users to be successfuly MITM'd and compromised.

  In addition, while SourceForge's download page is wrapped in TLS, they auto-redirect users to a download over HTTP. It is simply not possible to download binaries and SHA SUM's (or generate sums) from binaries downloaded insecurely over HTTP. Again, the issue isn't a problem that just SourceForge Therefore, there is no possible way that Formula maintainers can have any certainty whatsoever that the binaries they download and hash are not compromised, and that every Homebrew user who downloads from SourceForge isn't compromising their system by downloading from the site.

  HOWEVER, they do allow the source-code to be downloaded over a secure channel, so source syncs to GitHub, and unofficial mirrors of the binaries generated from the source hosted there would be a more secure alternative.

  This isn't a problem exclusive to SourceForge, though they may be the biggest offender. There are plenty of cases of files downloaded from other sites over HTTP, and FTP.

  That assumes the site even hosts a hash of the binary. Many others (and I'll pick on SourceForge because they're the oldest, and largest, among other things), do not, so hashes must be generated some other way, such as after the files are downloaded... and that's certainly another worthwhile coversation: how are hashes generated, verified, and could it be improved? Currently, ideally Formula maintainers are manually verifying that the hashes match prior to updating the Formula. Ideally, a distributed approach toward hash verification would be ideal, and either built in to Homebrew for everyone to contribute to (What SHA SUM did you receive? Let the community know!), or built in as a part of something that the maintainers, or project members would have access to. While granting access to everyone opens it up to large-scale attacks, keeping it closed opens it up to targeted attacks on project members, so it's somewhat of a question of which sort of attack the project would prefer to address. There's obviously a lot more that could be covered here, but I'll leave it at that for now.

- Along the lines of MITM attacks, the imperative for a .curlrc file does not seem to be widely known, or at least publicly discussed. In addition to ensuring a SHA SUM is present in ~/.&#91;shell&#93;&#95;profile, a .curlrc file must be used to ensure that the server you are connecting to allows a secure TLS connection to be made to it. 
  
  Not all forms of TLS are the same, and ensuring--by defining them in your ~/.curlrc file--that you're forcing an up-to-date protocol and set of ciphers is essential. A weak or outdated protocol or cipher suite could mean the server has been [or is easily] compromised, that your download is vulnerable to attack, and or that you yourself are open to compromise. 

  To loosely quote David's Law 'If something can be compromised it will be.', you're best off with an up-to-date .curlrc.


- TO DO: Homebrew also makes outgoing connections via Ruby (to GitHub).
Ensure that those sessions are forced on to a modern protocol and cypher suite (should be ok?).

- TO DO: Homebrew also makes outgoing connections via Python. 
Ensure that those sessions are forced on to a modern protocol and cypher suite.

- TO DO: Reference and/or briefly summarize the Cert Patrol-like Certificate Stapling user-land or daemon-level application writeup, and the attacks that it could prevent in these command-line cases.
