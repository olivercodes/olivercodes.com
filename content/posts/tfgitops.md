---
weight: 4
title: "WIP - Simple Terraform Gitops Workflow, w/ Prow and GH Actions"
date: 2021-12-20T00:00:00+00:00
lastmod: 2021-12-20T00:00:00+00:00
draft: false
author: "Bryan"
authorLink: "https://dillonzq.com"
description: "Work in progress - Terraform Gitops Workflow Guide"
featuredImage: "/lighthouse.jpg"
resources:
- name: "workflow"
  src: "/tfgit.jpg"

tags: ["Markdown", "HTML"]
categories: ["Markdown"]

lightgallery: true
---

## Requirements:

1. Prow Deployed - https://github.com/kubernetes/test-infra/blob/master/prow/getting_started_deploy.md
2. Owners files in your terraform repo
3. Access to an S3 bucket or similar (Minio, etc)


## Overview, the workflow


![/tfgit.jpg](/tfgit.png)

## Phase 1

### Init
``` 
TODO
```

We have a couple things happening during the init phase. 
- pulling down our terraform modules
- setting up the backend storage folder in s3 (plan output and state will go here)

### Make Plan
```
TODO
```

Here we are
- Formatting the terraform berfore run
- Running a quick check to see if the terraform is even valid (no point running plan if so)
- Generating the planfile and pushing it to s3




