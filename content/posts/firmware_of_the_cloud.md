---
weight: 4
title: "Terraform is just the firmware of the cloud"
date: 2024-12-16T00:00:00+00:00
lastmod: 2024-12-16T00:00:00+00:00
draft: true 
author: "Bryan"
authorLink: "https://olivercodes.com"
description: "How we write and approach IaC has to change. Approaching cloud engineering from a new perspective."
featuredImage: "/bmwmouse.jpg"
resources:
- name: "fwtoapi"
  src: "/fwtoapi.png"
- name: "bmwmouse"
  src: "/bmwmouse.jpg"
- name: "snow"
  src: "/snow.png"
- name: "pr"
  src: "/pr.png"
- name: "downtheroad"
  src: "/downtheroad.png"
- name: "apifirst"
  src: "/apifirst.png"
- name: "snow"
  src: "/snow.png"

tags: ["terraform", "iac", "kubernetes"]
categories: ["Markdown"]

lightgallery: true
---

## Stop starting with IaC

![/bmwmouse.jpg](/static/bmwmouse.jpg)
- Image credit: https://www.bmwblog.com/2012/08/31/bmw-rolls-out-high-end-computer-mouse-99/ 

When designing a brand new mouse, would you write the drivers or the firmware first? You would design the mouse! How many buttons does it have?
What sort of shape will it be? Who is the intended audience? What colors will we offer? Is it customizable? Is it heavy or light? All of these details factor in to the 
user interface of the mouse, and how it will be used by the customer. The underlying details of the mouse, are developed after the initial interface 
and design phase.

In my years, I've seen many companies that adopted Infrastructure as Code as a primary goal of their IT org. Initially, these initiatives are focused on taking manual processes or
script based provisioning and converting these cases into terraform. The end-goal often is a "self-service" set of terraform modules or repos where 
teams can create a pull request to get resources provisioned.

## IaC Shortcomings

![/snow.png](/snow.png)

How different is a pull request from a servicenow ticket? Changes are requested, reviewed, often assigned and reassigned. Eventually they are
approved or declined. 


![/pr.png](/pr.png)

The only major differences between a servicenow ticket and a pull request are the UI in which the change is requested, and the 
requestor takes a stab at "implementing" the change - all this because we say it's faster! 

The value of IaC itself is fairly well documented (consistency, auditability, testability, etc.) and I do not intend to debate it. But starting with only a focus on IaC is a massive mistake. Pull request based workflows
are a very low quality self-service experience, that barely differentiates itself from centralized devops processes.

Maybe it is a little faster, but the level of effort required to implement this sort of self-service capability often isn't worth the end state. As shown, we end up with a similar pattern that we had before. The value of IaC may be enough to warrant replicating our previous operational patterns, but I'd argue there are better ways to gain those IaC benefits and improve our workflows. 

## Treat Terraform as a minor detail

> When faced with two or more alternatives that deliver roughly the same value, take the path that makes the future easier - Dave Thomas

![/fwtoapi.png](/fwtoapi.png)

When we start with a design at the terraform layer, we miss an opportunity to define an abstract interface, one that doesn't bind us to a specific technology.
What if Terraform isn't what we want to use in 5 years? We'll have to rewrite all of those custom providers and modules. And while AI is making rewrites 
easier and easier, it's best if we avoid them completely when it's possible.

![/apifirst.png](/apifirst.png)

So what if instead, we defined our API first? The terraform is then the implementation of that API.

You can interpret the diagram how you want. For example the Terraform Cloud box above code, code be replaced with just standard compsite Terraform Modules being run in a CI system. And the underlying code layer could be custom providers, or vendor ones. Resource controllers might be any form of open source project that provides resource reconciliation and state (like custom crds in kubernetes, crossplane, rendered helm charts, etc.). 

The important aspect, is that our API in front of these layers is an abstract and self-service API consumeable by our engineers. 


![/downtheroad.png](/downtheroad.png)

Then, we can go on to write the implementation details of our API, such as the controllers, providers, modules, and terraform code that creates our resources. And now, when 
we decide we don't like Terraform, the consumers of our self-service platform don't have to care. We can change the underlying implementation without affecting them, or at 
least greatly reducing how much it affects them!





