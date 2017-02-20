##NoScript

1.) Not All TLS Protocols and Cipher Suites Are The Same

Assuming that users have NoScript configured properly and the only scripts being allowed to run are either on:
- Sites with some form of transport layer security enabled, or...
- Sites without TLS hosted locally (http://127.0.0.1/), or...
- On very small and secure LAN's (the fewer computers the better)...

A very useful feature to include would be:
- On the drop-down menu, allow users to see information about the TLS connection (protocol + cipher suite) that the site they're being asked to enable scripts on is serving them over.
- It would also be useful for less savvy users who may not have modified their browser configuration settings to restrict the protocols and cipher suites over which they will accept connections to also have a grading system--e.g. a color code such as Red, Yellow, and Green--to allow less-savvy users to know which protocols are considered reasonably safe and which are not.

1a.) No TLS Implementation is Without Flaw

Even the "latest and [thought to be] greatest" implementations of TLS aren't always safe to use; they can and are often implemented incorrectly. For this reason, another great feature to have, and the reason this is labeled (1a), would be to incorporate the latest tools released by researchers to test and verify the TLS implementation for correctness ([nonce reuse][0], was a recent issue at the time this was originally written), so that users aren't [given an entirely false sense of security about their TLS connection][1].

<html>
  <body>
    <text>
      &#91;0&#93;&nbsp;"Nonce reuse was a recent disclosed issue at the time this was originally written"&nbsp;-&nbsp;&#91;<a href="https://gcm.tlsfun.de/">https://gcm.tlsfun.de/<a/>&#93;<br/>
      &#91;1&#93;&nbsp;"Vulnerabilities to compromise servers via flaws in TLS implementations aren't unheard of. CloudFlare et al. allow servers to send unencrypted traffic to them, whereupon they then encrypt it, relay it on to the end-user, leaving a number of hops open for compromise, and the end-user's none the wiser, and on."&nbsp;-&nbsp;&#91;<a href="https://www.google.com/">https://www.google.com/<a/>&#93;<br/>
    <text/>
   <body/>
<html/>

2.) Context-Dependent Approval of Scripts (Temporary or Permanent):

2a.) Per-Tab
When I enable a script on one website, I don't want it auto-enabled on all of the other pages that I have loaded in the current browser session as well.

2b.) Per-Site
Along the lines of "Per-Tab" enabling of scripts, but different, on some sites I want some scripts to load whereas on other sites I don't want them to load. If I'm using Gmail or Google Drive and have all of the necessarily scripts enabled (or a better example might be if I've logged in to my Google Analytics platform), I don't necessarily want them auto-enabled on every website that I visit within that browser session (and with Google Analytics I DEFINITELY don't want them enabled. Funny how that works, isn't it? I wan't Google Analytics on my sites to slice, dice, and give me information about my users, but I, personally, have no desire for Google to track me via their Analytics system). Really though, I'm planning on using a stand-alone solution I can deploy without having to share it with a 3rd party, but for now the sites are small and Google Analytics is quick, easy, and gets the job done... and you're free to block the scripts on my sites (as I, and most tech-savvy people do on yours) if you don't wish to be tracked.

2c.) Per-script
Enabling scripts on a per-script basis would really be ideal. Currently, the only options are to permanently or temporarily allow scripts from a specific host. This ties strongly in to the next point (2d), as well as the "JavaScript AntiVirus", or "JS Hashing and Distributed Verification" system I describe in a different document, and may be something that could be integrated into this project. The features described in that document would allow users to have some sense of certainty that the programs (JavaScript) they ran within their browser were safe, as best as they could be assessed to be.

2d.) Per-Page
Site, or domain-wide enabling of scripts can be a risky proposition, which is the default--and only-option of NoScript. If a script hidden far down from the root contains something malicious and I load that page, the script will be auto-executed in my browser because I have either temporarily enabled, or permanently enabled scripts on that site; I have given them wholesale permission to run anything within my browser(!).
