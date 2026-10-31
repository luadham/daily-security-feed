---
layout: post
title: "SVD-2026-1014: Compromised eMudhra Intermediate Certificate Authorities on Splunk Products - October 2026"
date: 2026-10-27 00:00:00 +0300
categories: [RSS]
tags: [pki, certificate-authority, supply-chain, advisory, splunk]
toc: true
---

Splunk advisory SVD-2026-1014 responds to the disclosure (Oct 17-20, 2026) that private keys for eight eMudhra intermediate CAs were effectively broken by a flawed April 2025 Key Generation Ceremony. The keys can reportedly be brute-forced in seconds, so anyone could issue certificates that chain to those CAs. Splunk says it does not use eMudhra certificates and that its own service and code-signing certificates were not compromised. It is still checking whether any eMudhra CA appears in product trust stores (Splunk Enterprise, Universal Forwarder, SOAR, AppDynamics, Observability, Cisco Secure Endpoint, XDR and others, all listed as 'Under Investigation'). Impact depends on whether an active network path loads the affected trust store and uses it to validate a remote certificate chain. A trust-store entry alone does not make a product affected. The advisory has little technical depth of its own, but it is useful as a trust-store exposure and PKI supply-chain advisory, with the underlying eMudhra research and Talos post as the primary sources.

[Read original article](https://advisory.splunk.com/advisories/SVD-2026-1014){: .btn .btn-primary }
