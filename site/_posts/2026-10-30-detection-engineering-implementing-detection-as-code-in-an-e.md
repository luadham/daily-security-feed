---
layout: post
title: "Detection Engineering: Implementing Detection-as-Code in an Existing Environment: Part 1 – Introduction and Concept"
date: 2026-10-30 16:46:20 +0300
categories: [RSS]
tags: [detection-engineering, detection-as-code, splunk, git, ci-cd]
toc: true
---

Part 1 of an NVISO case study on migrating an operational environment to Detection-as-Code. The starting point was detections fragmented by platform across several Git repos (e.g. Splunk `apps` directory with huge `savedsearches.conf` files containing retired fragments) plus YAML metadata on a file share and Atomic Red Team tests grouped per ATT&CK technique. This made reviews hard, since one change needed multiple PRs, and left data quality and coverage poorly visible. The goals are to restructure data around the individual detection, consolidate everything in GitHub as a single source of truth, and lay a foundation for automation, reporting and compliance integrations. The target design is a single detection repo with `detections`, `detections_retired` and `utils` folders, one folder per detection, and platform configs generated at deploy time. Platform repos keep only platform-specific config and deployment logic, with the main branch consumed by platform teams for releases, and development follows GitHub Flow with issues, a project board and one PR per change. This part is conceptual and process-focused, with no code or detection logic yet, so it is useful for teams planning a similar migration.

[Read original article](https://blog.nviso.eu/2026/10/30/detection-engineering-implementing-detection-as-code-in-an-existing-environment-part-1-introduction-and-concept/){: .btn .btn-primary }
