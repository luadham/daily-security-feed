---
layout: post
title: "The Last Proof of Human Craft: Forging a Microsoft Edge Full Chain with Logic Bugs Only!"
date: 2026-10-28 04:58:51 +0300
categories: [RSS]
tags: [browser, edge, chromium, uxss, pwn2own]
toc: true
---

Orange Tsai details his Pwn2Own Berlin 2026 Microsoft Edge sandbox-escape full chain, built entirely from logic bugs (five bugs plus two Windows features, no memory corruption), which won $175k and a Pwnie for Epic Achievement. The first bug is in Edge's `EdgeCAGuidanceNavigationThrottle`, a Browser Process navigation throttle triggered by navigating from a Microsoft origin like `login.live.com` to `https://guidance-ca-error/?email=...&switch_profile={url}`. If the email matches the profile, the browser calls Chromium's `Navigate()` with an attacker-controlled URL, reaching privileged targets such as `edge://settings`, `devtools://` and `javascript:`. Because `NavigateParams` is created without `source_contents`, `Navigate()` falls back to the currently active tab as both source and target (`CURRENT_TAB`). Delaying the trigger and switching tabs therefore runs the `javascript:` URL in another origin, such as `google.com`, giving a 'sourceless navigation' UXSS primitive. The post also highlights Navigation Throttles as an under-audited attack surface, with fewer than 20 of Chrome's 3,000+ CVEs in five years related to them. The excerpt is the start of the chain, and the later bugs are covered in the slides.

[Read original article](https://blog.orange.tw/posts/2026-10-the-last-proof-of-human-craft-browser-full-chain/){: .btn .btn-primary }
