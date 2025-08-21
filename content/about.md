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



|         CVE-ID |            Vendor |                         Components |                            Exploit primitive |                  Security implications |
|----------------|-------------------|------------------------------------|----------------------------------------------|----------------------------------------|
|  CVE-2024-6044 |            D-Link |              Eagle pro home router |                               Path traversal | Arbitrary file read (Network adjacent) |
|  CVE-2024-6045 |            D-Link |              Eagle pro home router |   Hidden functionality, Hardcoded credential |       RCE (Network adjacent, Pre-auth) |
| CVE-2024-45694 |            D-Link |                  DIR-X home router |                  Stack-based buffer overflow |                         RCE (Pre-auth) |
| CVE-2024-45695 |            D-Link |                  DIR-X home router |                  Stack-based buffer overflow |                         RCE (Pre-auth) |
| CVE-2024-45696 |            D-Link |                  DIR-X home router |  Hidden functionality, Hard-coded credential |                         RCE (Pre-auth) |
| CVE-2024-45697 |            D-Link |                  DIR-X home router |                             Misconfiguration |                         RCE (Pre-auth) |
| CVE-2024-45698 |            D-Link |                  DIR-X home router |                            Command injection |                    RCE (Authenticated) |
|   Not assigned |           Mongodb | libbson (part of Mongodb C driver) |                                       OOB RW |     Unspecified (Application-specific) |
| CVE-2025-24302 | Intel open source |                           TinyCBOR |                       Uncontrolled recursion |                      Denial-of-Service |
| CVE-2025-20025 | Intel open source |                           TinyCBOR |                  Improper character escaping |     Unspecified (Application-specific) |


## Contact

Feel free to reach out with any feedback:

{{< cards cols="1" >}}
  {{< card link="mailto:linraymond2006@gmail.com" title="Primary/Personal Email" icon="mail" subtitle="linraymond2006\@gmail.com">}}
{{< /cards >}}

{{< cards cols="2" >}}
  {{< card link="mailto:b14902079@ntu.edu.tw" title="School Email" icon="mail" subtitle="b14902079\@ntu.edu.tw">}}
  {{< card link="mailto:raymond@ic3dt3a.org" title="Team Email" icon="mail" subtitle="raymond\@ic3dt3a.org">}}
{{< /cards >}}

OpenPGP public keys / Finger prints:

{{< cards cols="1" >}}
  {{< card link="/_resources/Raymond_linraymond2006@gmail.com-0x36ADCFB963D534FA-pub.asc" title="linraymond2006@gmail.com" icon="key" subtitle="FD1F BF75 466B FEAB B130 002A 36AD CFB9 63D5 34FA">}}
{{< /cards >}}

{{< cards cols="2" >}}
  {{< card link="/_resources/Raymond_b14902079@ntu.edu.tw-0x0545459CC38EBD82-pub.asc" title="b14902079@ntu.edu.tw" icon="key" subtitle="EBCA 1AAA 32EA 87D3 26DD EEEF 0545 459C C38E BD82">}}
  {{< card link="/_resources/icedtea.raymond_raymond@ic3dt3a.org-0x94160158CE4E268F-pub.asc" title="raymond@ic3dt3a.org" icon="key" subtitle="CCAA 513F D4C5 0DEF CFEF D249 9416 0158 CE4E 268F">}}
{{< /cards >}}

