---
title: TLS protocol
toc: false
---

## Motivation
tbd

## How it's done
tbd

## What I've learned
tbd (remember to place a card referring to code review in notes section)


## (Draft here)

- TLS protocol
	- record/message/extensions
	- handshake and handshake messages
	- hanshake messages and extensions
	- PKIX and certificate
	- ASN.1 DER/PEM and X.509 certificate format
	- how cryptography stuff works under the hood
- implementation: OpenSSL (TODO: port notes on hackmd.io here)
	- libssl, libcrypto(, and libbn) hierarchy and brief introduction
	- libssl deepdive
		- TUs and what type of functions they contain
		- layered approach: record handling layer, message handling functions, and extension handling callbacks
		- state machines: read/write FSM, handshake state FSM, sub-FSMs
		- PACKET and WPACKET interface
		- how it interact with libcrypto
	- libcrypto deepdive? (there's almost nothing to discuss)
		- how ASN.1 is parsed (source code tracing, seems boring)
		- how certificate is verified
		- how cryptography operation is performed (mostly signature stuff)
- implementation: wolfSSL
