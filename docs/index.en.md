---
description: Quor is a catalog of secure container images with zero or near-zero CVEs, signed and SBOM-backed for production-grade software supply chain security.
keywords: container security, secure container images, CVE-free images, SBOM, software supply chain, Kubernetes
---

# About Quor

## The challenge of container security

Quor was born from **hands-on experience in Kubernetes environments, especially in mission-critical companies**, closely observing how the **high volume of vulnerabilities (CVEs)** became a burden for development and security teams.

This volume drains resources, delays deliveries, and increases exposure to attacks; especially when companies use images whose origin and component integrity are unknown.

**Quor’s vision is clear**: reduce the attack surface and prevent CVEs, while increasing visibility and traceability across the software supply chain.

## What Quor is

Quor is a **catalog of secure container images, free of known CVEs and production-ready**.

These images are built from minimal bases, with **digital signatures** and **SBOMs (_Software Bill of Materials_)** that ensure integrity and traceability of every component included in each image. Excess software is removed, making the images lighter, more secure, and more performant.

As a result, Quor’s catalog images are published with **zero or near-zero known vulnerabilities** and accumulate flaws at a much slower rate over time when compared to official images.

## How Quor helps in practice

With Quor, teams start working with a **trusted catalog of container images**, instead of relying on images of uncertain origin or chosen for convenience.

This brings immediate benefits:

- **Less noise**: vulnerability triage is no longer a bottleneck, since images enter your pipeline with zero or near-zero known CVEs.
- **Lower supply chain risk**: provenance is clear, with integrity guaranteed by signatures and SBOMs.
- **Reduced dependency on third parties**: fixes are not tied to the original project’s schedule; they are applied continuously to the catalog.

The result is a much more secure and predictable production environment, without the burden of manually remediating upstream vulnerabilities and with reduced exposure to attacks.

!!! note

    The name Quor comes from the idea of being the **_'core'_ of container image security**.  
    Its mascot, the hedgehog, reflects this vision: a discreet animal with a highly sophisticated defense system.
