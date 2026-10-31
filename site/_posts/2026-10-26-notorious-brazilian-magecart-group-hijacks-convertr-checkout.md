---
layout: post
title: "Notorious Brazilian Magecart group hijacks Convertr checkouts via outdated Plausible install"
date: 2026-10-26 00:00:00 +0300
categories: [RSS]
tags: [supply-chain, magecart, skimmer, web-skimming, plausible]
toc: true
---

A Brazilian Magecart group active since 2024 appended an obfuscated skimmer to the Plausible analytics tracker script on Convertr's self-hosted server (analytics.convertr.app.br). Convertr runs the checkout for dozens of Brazilian fashion brands, and every merchant loads that one file. Sansec suspects the server was compromised through CVE-2026-8467 in an outdated Plausible Community Edition install. The payload is the stock Plausible script followed by character-code-obfuscated JavaScript run via eval. It activates only on checkout.convertr pages, scrapes card number, expiry, CVV, holder name and CPF from the payment form and the checkout's payment API requests, and POSTs them base64-encoded to 1x0.is/ws using fetch with no-cors and keepalive. The attacker updated it within two days: the 24 Oct version used generic field patterns, and a later version targeted the exact field names of Convertr's payment API. Convertr cleaned the script and patched Plausible by 27 Oct, after serving the skimmer for days without responding to Sansec. The same group has infected Magento, OpenCart and WooCommerce stores since July 2024, some for nearly two years.

[Read original article](https://sansec.io/research/convertr-plausible-supply-chain-attack){: .btn .btn-primary }
