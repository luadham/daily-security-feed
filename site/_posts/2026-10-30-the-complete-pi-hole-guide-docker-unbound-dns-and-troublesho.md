---
layout: post
title: "The Complete Pi-hole Guide: Docker, Unbound DNS, and Troubleshooting"
date: 2026-10-30 02:29:22 +0300
categories: [RSS]
tags: [dns, pihole, unbound, docker, homelab]
toc: true
---

A hub page indexing guides for running Pi-hole with Unbound as a fully recursive DNS resolver in side-by-side Docker Compose containers, so queries resolve from the root nameservers rather than via Google or Cloudflare. It links to setup and DNS configuration guides and to two troubleshooting write-ups: SERVFAIL on AWS Console domains, and slow cold-cache lookups. The slow-DNS guide measures latency layer by layer, covers an Unbound crash caused by a backward clock jump, and fixes both with DNS-over-TLS forwarding and continuous time sync. The FAQ lists common SERVFAIL causes (DNSSEC validation failures, blocked UDP/53, Docker internal DNS interference) and the commonly used images (mvance/unbound, klutchell/unbound). It is a defensive and privacy-oriented homelab configuration resource with limited security research depth, since the detailed content sits on the linked pages.

[Read original article](https://www.uncommonengineer.com/docs/engineer/LAB/pihole-guide){: .btn .btn-primary }
