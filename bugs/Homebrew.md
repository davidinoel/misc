## Homebrew - First Published: 20170220

#### INTRO:
Based on how long it's taken for the bug report describing the issue of adding the "--require-sha" flag to ~/.&#91;shell&#93;&#95;profile's HOMEBREW_CASK_FLAGS, it breaking of the `brew cask search` command to be filed, and its recognition among the tech community, it's surprising that this and other similar conversations didn't come up far sooner.

- There's a valid conversation that needs to take place about the way hashes are obtained, and their reliability. If a download URL is using HTTP, FTP, or some other insecure protocol, and the an attacker is sitting a hop or two in front of the download site, it's trivial for both the download file and the hash itself to be compromised, with neither the package maintainer nor most Homebrew users being any the wiser. In this scenario, the maintainer would download the compromised package and corresponding hash (or generate it on their end), and update the Formula with the corresponding sum and link, push it live, and allow millions of Homebrew users to update their systems, become successfuly MITM'd, and compromised.

    % cd /usr/local/Homebrew/Library/Taps/homebrew
    % grep -r "url \"http\:" | wc -l
    1159
    % find . | grep "\.rb" | wc -l
    5691

    1159/5691 ~= 20%

- That assumes the site even hosts a hash of the binary. Many others do not (and I'll pick on SourceForge because they're the oldest, and largest, among other things), so hashes must be generated some other way, such as after the files are downloaded.

  ...and that's certainly a separate, worthwhile coversation: how are hashes generated, verified, and could that process be improved? Under the currrent model, ideally Formula maintainers are manually verifying that the hashes match their downloads prior to updating the Formula. In the future, a distributed approach toward hash verification would be ideal, and either built in to Homebrew for everyone to contribute to, or built in as a part of something that the maintainers, or project members would have access to. The reasons to consider the different approaches are that while granting access to everyone opens the project, and thus the entire network up to large-scale attacks, keeping it closed to a select few opens it up to targeted attacks on those few, so it's somewhat of a question of which sort of attack the project would prefer to take on; which they feel most capable of mitigating. There is obviously a lot more that could be covered under that, but I'll leave it there for now.

  In addition, while SourceForge's download page is wrapped in TLS, the project pages, release pages, and download pages lack signatures for the binaries, and the site auto-redirects users to download them over HTTP. This makes it impossible for binaries to obtained from them securely.

  However, they do allow the source-code to be downloaded over a secure channel, so if the SourceForge, or other location hosted projects' build flags are known, and reproducible builds are possible, either building the project from source and ensuring the sums are correct, source-syncs to GitHub (unofficial mirrors), or providing a downloadable version in the unofficial-official mirror...small teams independently generating builds with default flags, hashing them(reproducible builds on osx?)

  This isn't a problem exclusive to SourceForge, though they may be the biggest offender. There are plenty of cases of files downloaded from other sites over HTTP, and FTP.

  

- Roughly 20% of Homebrew Cask Formula's currently contain "sha256 :no_check", meaning that not only do they lack the basic layer of security most would expect from a package manager by not allowing Caskroom to verify their sha256 signatures, but that if end-users were to set the --require-sha flag in the above file, ~20% of the software packages available via Caskroom would be unavailable to them because the signatures are not provided in the Formula.  

    % cd /usr/local/Homebrew/Library/Taps/caskroom  
    % find . |grep "\.rb" | wc -l  
    3779  
    % grep -r "sha256 :no_check" | wc -l  
    761  
    
    761/3779 ~= 20%  

- Along the lines of MITM attacks, the imperative for a .curlrc file does not seem to be widely known, or at least publicly discussed. In addition to ensuring a SHA SUM is present in ~/.&#91;shell&#93;&#95;profile, a .curlrc file must be used to ensure that the server you are connecting to allows a secure TLS connection to be made to it. 
  
  Not all forms of TLS are the same, and ensuring--by defining them in your ~/.curlrc file--that you're forcing an up-to-date protocol and set of ciphers is essential. A weak or outdated protocol or cipher suite could mean the server has been [or is easily] compromised, that your download is vulnerable to attack, and or that you yourself are open to compromise. 

  To loosely quote David's Law 'If something can be compromised it will be.', you're best off with an up-to-date .curlrc.


- TO DO: Homebrew also makes outgoing connections via Ruby (to GitHub).
Ensure that those sessions are forced on to a modern protocol and cypher suite (should be ok?).

- TO DO: Homebrew also makes outgoing connections via Python. 
Ensure that those sessions are forced on to a modern protocol and cypher suite.

- TO DO: Reference and/or briefly summarize the Cert Patrol-like Certificate Stapling user-land or daemon-level application writeup, and the attacks that it could prevent in these command-line cases.
