---
layout: post
title: "Slow DNS with Pi-hole + Unbound: Fixing Cold Lookup Latency"
date: 2026-10-30 02:29:22 +0300
categories: [RSS]
tags: [dns, pi-hole, unbound, dns-over-tls, homelab]
toc: true
---

A homelab troubleshooting write-up on intermittent page stalls traced to cold DNS lookup latency in a Pi-hole (v6) + Unbound setup on a Raspberry Pi 2 in New Zealand, not Wi-Fi. Unbound was doing full recursion, so each cache miss walked root → TLD → authoritative (root servers 140–220 ms away, plus DNSSEC DS/DNSKEY fetches and QNAME minimisation). The result was a median cold lookup of ~500 ms (worst 1.5 s) against 4–9 ms for cached lookups, and Unbound's own stats showed a median recursion time of 204 ms per miss. A secondary finding is that Unbound crashed on an internal assertion at the same second DietPi's daily time sync stepped the clock backwards, which restarted it with an empty cache. The fix was to switch Unbound to DNS-over-TLS forwarding (Cloudflare + Quad9) and enable continuous time sync, cutting the cold median to ~150 ms and the worst case to ~620 ms. It also notes that a UniFi gateway DNS lockdown blocks external DNS/DoT/DoH from LAN clients, which affects Chrome's secure DNS settings. The article is operational and has little security-research value.

[Read original article](https://www.uncommonengineer.com/docs/engineer/LAB/pihole-unbound-slow-dns){: .btn .btn-primary }
