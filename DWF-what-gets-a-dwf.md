# What gets a DWF ID?

Any weakness that results in a vulnerability that an attacker can meaningfully exploit.

The attacker must be able to trigger the vulnerability in order to cross some sort of trust boundary and have a meaningful effect. It can be a privilege escalation, seeing information they should not have access to, or crashing the system remotely.

Like most things in life there is a spectrum ranging from "obviously this needs a DWF ID" to "this is clearly not a security issue" to "it's somewhere in the middle" some simple examples:

## Definitely needs a DWF ID:

Ping of death v2 (CVE-2020-16898 and CVE-2020-16899) a ping packet sent remotely crashes Windows.

## Probably needs a DWF ID 

Establishing 10,000 connections to a web server that explicitly claims to support 10,000 connections crashes it. Effectively a promise/guarantee was made that is being broken.

An administrative account is embedded in the system with a default password that can be changed, but does not force or encourage the user to change it. This will likely result in an exploitable vulnerability.

## Maybe needs a DWF ID 

Establishing 1,000 connections to a web server that does not make explicit claims about how many connections it supports or under what circumstances makes the web server extremely slow to respond. What about 500 connections? 100? 10? At some point we can agree "10 connection slows the server to a dead crawl is a problem" but what is the upper bound on this? Our suggestion is you file a request so it can be further investigated, researched and discussed.

Official documentation that encourages the use of a known vulnerable configuration, especially when a known secure configuration is available.

Source code and configuration examples that include vulnerabilities, for example SQL code in a textbook that includes an SQL injection vulnerability.

## Definitely does NOT need a DWF ID:

A 100 gigabyte file that when loaded into an image editing program results in a large amount of memory being used. That's just how things work.

# Common problem cases

## Local program crashes

If a file crashes a locally executed program this is generally not DWF ID worthy, unless it completely crashes a program that is commonly handling other data, files or tasks causing a denial of service effect that is noticeable to the user. If the file simply cannot be loaded properly and no other real effect occurs than the simple answer is "it's a broken file, it causes no problem, it just can't be loaded, to bad."

## Fuzzer/Fuzzing results

Fuzzer/Fuzzing results vary tremendously in quality and quantity. As such it is highly unlikely that EACH fuzzing results needs a DWF ID, they need to be properly researched and merged depending on their root cause. Additionally unless a fuzzing result causes an obvious security issue such as remotely crashing a network server it needs to be further researched to determine if there is any meaningful security impact from the fuzzing result. In short with fuzzing results you need to 1) show a security impact and 2) if you have multiple results show that they are unique to some degree (e.g. different file types, crashes with different error messages, etc.)
