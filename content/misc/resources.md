---
title: Learning resources compilation
---

These are some cool/useful resources I find helpful when learning.

> [!NOTE]
> 1. These are my personal opinion, which might vary between individuals. These stuff might be cool and engaging to me but not to you!
> 2. There are some Chinese stuff that I read (since I'm a Taiwanese), Chinese will be used regarding these.
> 3. The entries are not sorted; some well-known stuff are not listed here.
> 4. Some resource might be paid (and even expensive) :(

## Epic books

- TCP/IP illustrated
	- There are three volumns, but Vol 1 is GOAT among three!
	- Volumn 1 introduces how the network works, from overall concept to gory details. This is a must-read for someone learning networking for the first time!
	- Volume 2 traverses the source code of the BSD kernel. However, it's annotating an ancient version, and there have already been better designs and implementations. Nonetheless, it's still worth reading if you're interested in how some socket features on *NIX systems were initially designed.
	- Volume 3 elaborates on T-TCP, NNTP, and UNIX sockets. It's suitable for those who want to know more about UNIX sockets.
	- TCP/IP illustrated explains the most essential parts of the TCP/IP networking stack. It's probably reasonable to experience information overload during your study session.
- Arm Assembly Internals and Reverse Engineering (Blue Fox Edition)
	- The perfect book for learning ARM assembly and hardware properties (and all the cool stuff). This book helped me learn ARM when I was used to x86's CISC instruction set.
	- Author of the book is also the founder of Azeria labs, some amazing tutorials can be found on their [official website](https://azeria-labs.com/writing-arm-assembly-part-1/)
	- Seems red fox edition (which is about offensive technique on ARM platform) is not available, information can't be found on the web...
- Practical Malware Analysis: The Hands-On Guide to Dissecting Malicious Software
	- Very useful in learning malware reverse engineering.
	- Shows some techniques used by malware for detection evasion, obfuscation, etc.
	- Be sure to do the exercises for every chapter, those question-answer style exercises truely provide a guided method to understand what's happening under the hood.
- Learning Linux Binary Analysis
	- Contains everything you need to know about ELF. This book assisted me understand how ELF symbol resolution works (which is prerequisite for ret2dl attacks)
	- It's a thin book!
- Reverse Engineering for Beginners (also known as RE4B)
	- Provides substaintial amount of code snippets and C-assembly mappings across various mainstream processor architectures, compilers, and operating systems.
	- Shows some bit hacks and compiler optimizations at instruction level, cool!
	- (In my opinion) it's probably not so suitable for beginners with zero prior knowledge, build a solid C and assembly basis first and start reading!
	- There're also some cool stuff on [author's blog](https://yurichev.com/)
- 資安這條路：領航新手的 Web Security 指南，以自建漏洞環境學習網站安全
	- 講述了網頁安全的基礎，完全沒概念的人必看！
- A Guide to Kernel Exploitation: Attacking the Core
	- Might need some background in kernel stuff (driver, kernel module, how kernel works with hardware internally, etc).
	- Shows some cool techniques that increase the success rate when exploiting the kernel, also demonstrates some extremely sophisticated novel attack against the kernel.
	- Though the kernel in question is outdated for a long time, most technique still applies.
- Windows internals
	- The authoritative book about Windows system's kernel
	- Experience with native Windows application developement will be very beneficial.
	- Information overloadddd... (Still don't have a clear idea about the content)
- FYSOS series
	- There are several books in this series:
		- FYSOS: The Graphical User Interface
		- FYSOS: The System Core
		- FYSOS: The Virtual File System
		- FYSOS: Input and Output Devices
		- FYSOS: The Universal Serial Bus
		- FYSOS: Media Storage Devices
	- Most of these books are great; however, the most unique one is "FYSOS: The Universal Serial Bus," which will teach you how the USB controller and the ACPI work in theory, and how to manipulate those in practice (there're few books in this topic). There's considerable amount of nasty hardware specs for you to process, you might undergo information overload.
		- I still don't fully understand how it works :(
- Linux 網路內功修煉 - 徹底了解底層原理及高性能架構
	- 非常深入且容易理解的分析 Linux kernel 如何處理網路封包和連接。
	- 每個節前都會放出一些問題給讀者思考，最後會給出答案，能快速的解開心中的疑惑。
- 一個 64 位操作系統的設計與實現
	- 市面上少數用中文寫的作業系統開發的書。
	- 參考早期 Linux kernel 的實做，內容寫得很不錯。
	- 內容滿豐富的（還包括了 SMP 的主題），對於 OSdev 有興趣的人一定要買來看看。
- Computer Organization and Design
	- The one I read is MIPS edition, 2/e, there're RISC-V edition out there now.
	- A must-read for those who interested in computer organization and architecture
	- TODO: haven't tried "Computer Architecture: A Quantitative Approach", make a comparison after reading!
- 漏洞戰爭：軟件漏洞分析精要
	- Windows 平台上商用軟體和瀏覽器的漏洞成因及 exploit 非常深刻的分析。
- 程序員的自我修養：鏈接、裝載與庫
	- 不僅有動態連結、靜態連結所有需要的知識，還完整講解了不同平台上的執行檔格式（PE 和 ELF），這本書必須買來看。
- SSL and TLS: Theory and Practice
	- Virtually everything you need to understand SSL/TLS (and start investigating protocol stack implementations lol).
	- Explain differences between versions.
	- You need not to have backgrounds in SSL/TLS protocol, this book is completely beginner-friendly.
- C++ Primer
	- This is NOT the same as C++ Primer plus (haven't read primer plus yet)
	- TODO: Not finish reading yet...
- Introduction to Algorithms
	- TODO: Not finish reading yet...
- Concrete Mathematics
	- NOTE: too hard that I almost gave up reading...

## Epic articles, paper, and blog posts
- nothing here for now

## Cool links and useful utils
- nothing here for now

## Epic off-topic stuffs
- nothing here for now
