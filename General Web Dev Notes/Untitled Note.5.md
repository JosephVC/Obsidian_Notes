---

tags: 
  - domains
  - same-origin

---
**Same Origin Policy**

Websites that have the same combination of scheme, hostname, and port are considered to have the same origin.  Otherwise, the site is considered **cross origin.** 

![[./_resources/Untitled_Note.5.resources/web dev - same origin examples.jpg]]

**Top-level domains (TLD)** are the .com, .org, .net, etc of the Internet.  What makes up the rest of a **"site"** is what is just before the TDL- [example.com](http://example.com/)

This being said, there are sites where the TDL is not granular enough to identify the page as a "site".  Examples of this would be **.co.jp** or **.github.io.**  There's also no way to algorithmically determine the level of registerable domains for a particular TDL. .  Thus, the "effective TDL" list was created.  These are defined at the [Public Suffix List](https://wiki.mozilla.org/Public_Suffix_List) and maintained at <https://publicsuffix.org/list/>

The whole site name is the eTDL+1, which is the effective TDL and the site just before it.  Just like with the above same origin policy, sites that have the same eTDL+1 are considered trustworthy while those that don't, aren't.  

![[./_resources/Untitled_Note.5.resources/web dev - same origin with eTDL-1.jpg]]

**Schemeful same-site**

There are times when the scheme of site needs to be paid attention to in order to prevent the HTTP protocol from being a weak channel.  the **scheme** here is whether the full site name begins with **http** or **https**.  

![[./_resources/Untitled_Note.5.resources/web dev - same origin with eTDL-1.jpg]]

The way to test for all this is to look at the HTTP header.  Chrome uses Sec-Fetch-Site as a way to do this.
