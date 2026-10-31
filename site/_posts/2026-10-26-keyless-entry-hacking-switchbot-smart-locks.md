---
layout: post
title: "Keyless Entry: Hacking SwitchBot Smart Locks"
date: 2026-10-26 00:00:00 +0300
categories: [RSS]
tags: [iot, smart-lock, bluetooth, aes-ctr, cryptography]
toc: true
---

Neodyme found a cryptographic flaw in the BLE protocol of the SwitchBot Lock Pro smart lock series that lets an attacker open the lock with a software-only attack. Firmware pulled from a public S3 bucket referenced in the Android app showed that the outdoor key pad validates the PIN, fingerprint or fob and then sends an UNLOCK command to the indoor actuator. That link is plain BLE with a home-brewed application-layer scheme: the key pad and actuator share a secret key set at pairing, and a nonce that is reused for a whole session. Commands are encrypted with AES-CTR, which has no integrity protection, so ciphertext bit flips map directly onto plaintext bit flips. The key pad's lock button always sends an encrypted LOCK command, even when the door is already locked. An attacker can sniff that command and XOR in the constant difference between LOCK and UNLOCK, which is identical across sessions and devices and needs to be computed only once. The result is a valid encrypted UNLOCK that opens the door. SwitchBot has fixed the flaw and is rolling out firmware updates, and Neodyme withheld the full exploit because many devices are likely still vulnerable.

[Read original article](https://neodyme.io/en/blog/switchbot/){: .btn .btn-primary }
