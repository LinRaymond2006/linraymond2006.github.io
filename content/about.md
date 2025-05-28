---
title: About me
type: about
toc: false
---

Nothing to see here for now...

## I'm currently focusing/learning...

- C++ (and memory bugs)
- Malware developement
- DSA
- Code review on large OSS projects (abt 100k+ SLOC)

## Areas of interest

- Low level stuff
	- OSdev, Kernel, etc
	- C, Assembly (x86 family, ARM)
	- Network protocols (and their implementations)
- Program security
	- Binary exploitation (mainly on x86 but sometimes ARM)
	- Code review and bug hunting
	- Reverse engineering
- Video games heh :)

## Vulnerability reports

|         CVE-ID | Vendor |            Components |                            Exploit primitive | Security implications |
|----------------|--------|-----------------------|----------------------------------------------|-|
|  CVE-2024-6044 | D-Link | Eagle pro home router |                               Path traversal | Arbitrary file read (Network adjacent) |
|  CVE-2024-6045 | D-Link | Eagle pro home router |   Hidden functionality, Hardcoded credential | RCE (Network adjacent, Pre-auth) |
| CVE-2024-45694 | D-Link |     DIR-X home router | Stack-based buffer overflow | RCE (Pre-auth) |
| CVE-2024-45695 | D-Link |     DIR-X home router | Stack-based buffer overflow | RCE (Pre-auth) |
| CVE-2024-45696 | D-Link |     DIR-X home router |  Hidden functionality, Hard-coded credential | RCE (Pre-auth) |
| CVE-2024-45697 | D-Link |     DIR-X home router |                             Misconfiguration | RCE (Pre-auth) |
| CVE-2024-45698 | D-Link |     DIR-X home router |                            Command injection | RCE (Authenticated) |
|   Not assigned | Mongodb | libbson (part of Mongodb C driver) | OOB RW | Unspecified (Application-specific) |

## Contact

Feel free to reach out with any feedback:
{{< cards cols="1" >}}
  {{< card link="mailto:linraymond2006@gmail.com" title="Email" icon="mail" subtitle="linraymond2006 [at] gmail [dot] com">}}
{{< /cards >}}

PGP fingerprint
```plain
FD1F BF75 466B FEAB B130 002A 36AD CFB9 63D5 34FA
```

PGP public key
```plain
-----BEGIN PGP PUBLIC KEY BLOCK-----

xjMEZ5CeyxYJKwYBBAHaRw8BAQdANolty9hJjduvHr+YwpcXXejWIUVbYiXSrbGb
by1VAC3NIlJheW1vbmQgPGxpbnJheW1vbmQyMDA2QGdtYWlsLmNvbT7CiQQTFggA
MRYhBP0fv3VGa/6rsTAAKjatz7lj1TT6BQJnkJ7LAhsDBAsJCAcFFQgJCgsFFgID
AQAACgkQNq3PuWPVNPraBAD/ctg0/tzv8X0ifYqnVq1emcjjBYim6Eyl1/Tn2B2Z
e2YBAJ+x4BBTcPBTapsJ8Rq2S9xhiW+hOaLkjXnd/gDDkxoEzjgEZ5CeyxIKKwYB
BAGXVQEFAQEHQOMXWVVFKYi/1dZkCavVwFk5hY0xx7y8snLR+GgW8OFNAwEIB8J4
BBgWCAAgFiEE/R+/dUZr/quxMAAqNq3PuWPVNPoFAmeQnssCGwwACgkQNq3PuWPV
NPrHvQEA4rzk5Obo/p8Sc8IE/XnqvjFoDHwzbH0G9cc30AJsGkwA/RMhMmLbBtfr
E9sYwWhFuDMQsYqbo+fCHsF9wu8q9Q0O
=n7OW
-----END PGP PUBLIC KEY BLOCK-----
```
