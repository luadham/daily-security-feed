---
layout: post
title: "ElectroNG is now open source!"
date: 2026-10-26 23:00:00 +0300
categories: [RSS]
tags: [electron, sast, tool-release, static-analysis, open-source]
toc: true
---

Doyensec has open-sourced ElectroNG under Apache 2.0, a SAST scanner for Electron applications. It is split into a desktop app (project management, triage, reporting) and the ElectroNG-core scanning engine, which holds the checks, knowledge base, and Electron vulnerability database. Compared with the now-archived Electronegativity CLI, it offers improved HTML/JS/TS parsing, about 60 version-aware checks, a database of 650+ known Electron vulnerabilities, and an inventory of BrowserWindow/BrowserView security settings. It also supports in-app triage and exports to PDF, HTML, XLSX, CSV, and SARIF. Doyensec says the last substantial development was in 2024, so detection for modern Electron versions may be incomplete or noisy. It is asking the community to contribute updated checks, regression tests, and modernization work.

[Read original article](https://blog.doyensec.com/2026/10/27/electrong-oss.html){: .btn .btn-primary }
