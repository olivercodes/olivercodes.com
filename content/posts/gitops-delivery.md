---
weight: 4
title: "Cloud Native Delivery Patterns"
date: 2021-12-20T00:00:00+00:00
lastmod: 2021-12-20T00:00:00+00:00
draft: true
author: "Bryan"
authorLink: "https://olivercodes.com"
description: "Delivery patterns for cloud native applications"
featuredImage: "/lighthouse.jpg"
resources:
- name: "workflow"
  src: "/tfgit.jpg"

tags: ["gitops", "delivery"]
categories: ["Markdown"]

lightgallery: true
---

## Collecting patterns to review

- Pull based reconciliation (declarative backend, like git, is used by targets to meet desired state)
- Push based reconciliation (stateful backend, like a database, reconciles state of targets)
- Fire and forget, single try (attempt to do the thing, don't try again)
- Fire and forget, repeat (attempt to do the thing, and try again on a timer or state)
- PID?

## List of sub-topics to discuss

- evolution of CI
- Continuous Delivery
- Manual gating
- Canary
- BlueGreen
- RedBlack
- Gitops
