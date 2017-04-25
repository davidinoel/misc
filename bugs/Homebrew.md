## Homebrew

#### INTRO:
Based on how long it's taken for the bug report describing the issue of adding the "--require-sha" flag to ~/.&#91;shell&#93;&#95;profile's HOMEBREW_CASK_FLAGS and it breaking `brew cask search` to be filed, and its popularity among the tech community, it's surprising that this and other similar conversations didn't come up far sooner.

- There's a valid conversation that needs to take place about the way hashes are obtained and their reliability. If a download site is using HTTP and an attacker is sitting a hop or two above the download site, it's trivial for both the download file and the hash to be compromised and neither the Homebrew user nor the package maintainer to be any the wiser. The maintainer will download the package and hash, verify that they match, and then update the appropriate Formula with the corresponding sum and link, and millions of Homebrew users will be successfuly MITM'd.

  That assumes the site even hosts a hash of the binary. SourceForge, for example, along with many others, does not, so hashes must be generated some other way, such as after the files are downloaded. In addition, while their download page is wrapped in TLS, it auto-redirects users to a download over HTTP. It is simply not possible to download Homebrew binaries from SourceForge over a secure channel (I have found one, technically). Therefore, there is no possible way that Formula maintainers can have any certainty whatsoever that the binaries they download and hash are not compromised, and that every Homebrew user who downloads from SourceForge isn't compromising their system by downloading from the site.

  HOWEVER, they do allow the source-code to be downloaded over a secure channel, so source syncs to GitHub, and unofficial mirrors of the binaries generated from the source hosted there would be a more secure alternative.

  This isn't a problem exclusive to SourceForge, though they may be the biggest offender. There are plenty of cases of files downloaded from other sites over HTTP, and FTP.

- Along the lines of MITM attacks, the imperative for a .curlrc file does not seem to be widely known, or at least publicly discussed. In addition to ensuring a SHA SUM is present in ~/.&#91;shell&#93;&#95;profile, a .curlrc file must be used to ensure that the server you are connecting to allows a secure TLS connection to be made to it. 
  
  Not all forms of TLS are the same, and ensuring--by defining them in your ~/.curlrc file--that you're forcing an up-to-date protocol and set of ciphers is essential. A weak or outdated protocol or cipher suite could mean the server has been [or is easily] compromised, that your download is vulnerable to attack, and or that you yourself are open to compromise. 

  To loosely quote David's Law 'If something can be compromised it will be.', you're best off with an up-to-date .curlrc.


- TO DO: Homebrew also makes outgoing connections via Ruby (to GitHub).
Ensure that those sessions are forced on to a modern protocol and cypher suite (should be ok?).

- TO DO: Homebrew also makes outgoing connections via Python. 
Ensure that those sessions are forced on to a modern protocol and cypher suite.

- TO DO: Reference and/or briefly summarize the Cert Patrol-like Certificate Stapling user-land or daemon-level application writeup, and the attacks that it could prevent in these command-line cases.
