---
title: "Remote PwdHash"
date: 2019-03-13T14:01:15+08:00
categories:
  - "Miscellaneous"
tags:
  - "Miscellaneous"
---

<!--* Remote PwdHash Form
      * An HTML form that calls the JavaScript implementation of PwdHash
      * Version 1.0 Copyright (C) Stanford University 2004-2005
      * Contributors: Dan Boneh, Collin Jackson, John Mitchell, Nick Miyake, and Blake Ross
      * Distributed under the BSD License
      * See http://crypto.stanford.edu/PwdHash for more info.
      *-->

<script src="https://crypto.stanford.edu/PwdHash/RemotePwdHash0.8/md5.js" type="text/javascript"></script>
<script src="https://crypto.stanford.edu/PwdHash/RemotePwdHash0.8/pwdhash.js" type="text/javascript"></script>
<script src="https://crypto.stanford.edu/PwdHash/RemotePwdHash0.8/hashed-password.js" type="text/javascript"></script>
<script src="https://crypto.stanford.edu/PwdHash/RemotePwdHash0.8/domain-extractor.js" type="text/javascript"></script>
<body onLoad="Init();">
<table align="center" style="margin: 1em 1em 1em 1em;border:3px solid green;"><tr><td>
<form name="hashform" action="error.html" method="POST" onsubmit="setTimeout('GenerateToTextField()', 0); return false;">
<table id="theHashForm">

<td class="stepList">
<div class="step" id="theSiteDomain">

**Site Address**

<input type="text" name="domain">
</div>
<div class="step" id="theSitePassword">

**Site Password**

<input type="password" name="sitePassword">
</div>
</td>

<tr>
<td class="stepList" colspan="2">
<div class="step" id="theHashedPassword">

**Hashed Password**

  <span id="theGeneratePanel" >
    <input type="text" name="hashedPassword">
    <input type="submit" name="submitbutton" value="Generate">
  </span>

</div>
</td>
</tr>
</table>
</td>
</tr>
</form>
</table>
Version 0.8 ([more versions](https://crypto.stanford.edu/PwdHash/RemotePwdHash/))
<center>![Stanford](https://crypto.stanford.edu/PwdHash/stanford_seal64.gif)</center>  

PwdHash generates theft-resistant passwords.The PwdHash browser extension invisibly generates these passwords when it is installed in your browser.You can activate this protection by pressing F2 before you type your password, or by choosing passwords that start with <tt>@@</tt>.If you don't want to install PwdHash on your computer, you can generate the passwords right here.

* 8Visit the [Stanford project website](http://crypto.stanford.edu/PwdHash/).

* Install [PwdHash for Firefox](https://addons.mozilla.org/en-US/firefox/addon/pwdhash/). It has been ported to [Chrome](https://chrome.google.com/extensions/detail/dnfmcfhnhnpoehjoommondmlmhdoonca) and [Opera](http://www.coredump.gr/pwdhash-for-opera/).

* Read the [USENIX Security Symposium 2005 paper](http://crypto.stanford.edu/PwdHash/pwdhash.pdf) (PDF).

* This site and plugin are no longer under active development and the [code](http://github.com/collinjackson/pwdhash-website) is available for use. See individual files for license details.

Contributors: [Blake Ross](http://www.blakeross.com/),[Collin Jackson](http://www.collinjackson.com/),Nicholas Miyake,[Dan Boneh](http://crypto.stanford.edu/~dabo/) and [John C. Mitchell](http://theory.stanford.edu/people/jcm/home.html)

Another simple way to generate strong passwords is derived from xkcd: Password Strength.
<center>![Password Strength](https://imgs.xkcd.com/comics/password_strength.png)</center> 

Diceware is another passphrase generator following the proposals of Arnold G. Reinhold on http://diceware.com . It generates passphrases by concatenating words randomly picked from wordlists. 


Randall Munroe did offer us a solution: a Correct Horse Battery Staple. By memorizing a long phrase, a greater number of bits are more easily encoded in a user’s memory, making a password much harder to crack. ‘Correct Horse Battery Staple’ only provides a 44-bit password, though, and researchers at the University of Southern California have a better solution: prose and poetry. Just imagine what a man from Nantucket will do to a battery staple.

Correct Horse Battery Staple, Generate Secure Memorable Passwords. A secure password will help keep you safer online.
http://correcthorsebatterystaple.net/

Image credit xkcd(https://xkcd.com/)
</body>
