##Homebrew Issues

####INTRO:
Based on the recent timing of the bug report describing the issue of adding the "--require-sha" flag to ~/.[shell]_profile's HOMEBREW_CASK_FLAGS and it breaking `brew cask search`, it's surprising that no one's brought up any of the number of discussions that could come from this, and the use and observation of Homebrew's general behavior.

- There's a valid conversation that needs to take place the way hashes are obtained and their reliability. If a download site is using HTTP and an attacker is sitting a hop or two above the download site, it's trivial for both the download file and the hash to be compromised and no Homebrew user or the package maintainer to be any the wiser. The maintainer will download the package and hash, verify that they match, and then update the appropriate Formula with the corresponding sum and link, and millions of Homebrew users will be successfuly MITM'd. That assumes the site even hosts a hash of the binary. 

SourceForge, for example, does not, so hashes must be generated some other way, such as after the files are downloaded. In addition, SourceForge, while their download page is TLS-wrapped, redirects to an unprotected port 80 download page where the file is downloaded. They do however allow the source-code to be downloaded securely, so source syncs to GitHub, and unofficial mirrors of the binary hosted there may be a more secure alternative.

- Along the lines of MITM attacks, the need for a .curlrc file does not seem to be widely known, or at least discussed. In addition to ensuring a SHA SUM is present in the [~/.${shell}_profile], a .curlrc file should be used to ensure that the server you're connecting to allows a secure TLS connection to be made to it. 

Not all forms of TLS are the same, and ensuring (by itemizing in your ~/.curlrc file) that you're force-using an up-to-date protocol and set of ciphers is essential. A weak/outdated protocol/cipher suite could mean the server has been [or is easily] compromised, that your download is vulnerable to attack, and or that you yourself are open to compromise. 

To loosely quote David's Law 'If something can be compromised it will be.', you're best off with an up-to-date .curlrc.


- TO DO: Homebrew also makes outgoing connections via Ruby (to GitHub).
Ensure that those sessions are forced on to a modern protocol and cypher suite.

- TO DO: Homebrew also makes outgoing connections via Python. 
Ensure that those sessions are forced on to a modern protocol and cypher suite.

- TO DO: Reference and/or briefly summarize the Cert Patrol-like Certificate Stapling user-land or daemon-level application writeup, and the attacks that it could prevent in these command-line cases.
