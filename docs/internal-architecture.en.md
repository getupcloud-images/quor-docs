# Quor internal architecture

This page provides a high-level and more descriptive view of how Quor identifies vulnerable images, rebuilds them from source code, and keeps the catalog close to zero known CVEs over time.

![Quor internal architecture diagram](assets/diagram-en.png)

## Architecture goal

Quor is designed to solve a practical operational problem: teams need container images that are secure by default, continuously maintained, and ready to use in production without constant manual CVE triage.

To achieve this, Quor treats image security as a continuous lifecycle instead of a one-time scan.

## Main architecture blocks

At a high level, the architecture can be understood in four blocks:

1. **Vulnerability intelligence and correlation**  
   Quor continuously ingests vulnerability information and correlates CVEs with affected packages and image versions.

2. **Source-first image factory**  
   For remediation, Quor rebuilds images directly from source code with controlled inputs, instead of relying only on upstream prebuilt binaries.

3. **Security validation and attestations**  
   Each build is validated through vulnerability scans and policy checks, then accompanied by security artifacts such as SBOMs, signatures, and provenance metadata.

4. **Registry publication and feedback loop**  
   Approved images are published to the Quor registry and kept under continuous monitoring, so newly disclosed CVEs can trigger a new remediation cycle.

## End-to-end flow

The flow is iterative and continuously repeated:

1. **Detect risk**
   - Identify newly disclosed CVEs and map them to catalog images.
   - Locate the exact vulnerable component (package, dependency, or layer).

2. **Plan remediation**
   - Decide whether to update, patch, or replace the vulnerable component.
   - Define the safest path to reduce exposure while preserving expected behavior.

3. **Rebuild from source**
   - Build updated components and image layers from source code.
   - Keep the image minimal to reduce attack surface and unnecessary packages.

4. **Validate and attest**
   - Re-scan the image for known vulnerabilities.
   - Generate and publish SBOM, signature, and provenance artifacts.

5. **Publish and monitor**
   - Release the updated image version in the Quor registry.
   - Continue monitoring for newly disclosed CVEs and restart the cycle when needed.

## Why rebuilding from source matters

- **Remediation speed**: fixes are not blocked by external image release timing.
- **Tighter control**: build inputs and resulting artifacts are controlled and auditable.
- **Lower residual risk**: minimal images and continuous revalidation reduce long-term vulnerability accumulation.

The outcome is a practical security baseline for platform and application teams: production-ready images that stay at zero or near-zero known CVEs for as long as possible.
