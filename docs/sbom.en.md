# SBOM

## Introduction

SBOM (Software Bill of Materials) is a structured inventory of everything that composes a software artifact.
It is not only a dependency list. A production-grade SBOM includes metadata such as:

- Component name and version
- Supplier/source
- License
- Cryptographic hashes
- Dependency relationships
- Standard identifiers (for example PURL and CPE)

In practice, SBOM data can be modeled as a dependency graph that enables transitive impact analysis and continuous vulnerability correlation over time.

The most common formats are SPDX and CycloneDX:

- SPDX started with license/compliance focus
- CycloneDX started with stronger application security focus

Both are widely used and supported by modern tooling.

## Why SBOM is foundational for security

When incidents like Log4Shell happen, teams need immediate and precise answers:

- Where is the affected component?
- Which image versions are impacted?
- What is already fixed?

Without SBOM, this is often manual and slow. With SBOM, the inventory is already materialized and can be continuously re-evaluated against vulnerability feeds (NVD, OSV, GHSA) without rebuilding the image.

This reduces triage noise and improves response time.

## SBOM in Quor

In Quor, SBOMs are generated during build and published with each image version as part of the security evidence set.
They are distributed together with signatures and provenance metadata.

You can download an SBOM in the UI:

1. Open the image catalog.
2. Select an image.
3. Open the **SBOM** tab on the details page.
4. Select version and architecture.
5. Download the SBOM file.

## Relationship with VEX, provenance, and SLSA

SBOM answers **what is inside** an image.
It does not, by itself, answer:

- If a CVE is exploitable in that runtime context
- How the image was built and by whom
- What software supply chain guarantees are enforced

For that reason, SBOM should be consumed together with:

- **VEX**: exploitability status and technical justification per CVE (`not_affected`, `affected`, `fixed`, `under_investigation`)
- **Provenance attestations**: verifiable build origin metadata (source repository, commit, builder identity, build timestamp)
- **SLSA-aligned controls**: maturity model for reproducible and trustworthy build pipelines

This layered model turns static inventory into actionable and auditable trust evidence.

## Practical note: scanning SBOM vs scanning OCI image

For many pipelines, scanning a generated SBOM is faster than rescanning the full OCI image every time.
The package inventory is already enumerated, so scanners can focus directly on vulnerability correlation.
This approach improves scalability and keeps build and vulnerability analysis decoupled.

## Scope and limitations

SBOM is essential, but it is not a complete security model:

- It focuses mainly on third-party composition
- It does not replace SAST/DAST, threat modeling, or code review
- It does not prove authenticity unless tied to signature/attestation workflows

Quor treats SBOM as a core building block in a broader evidence-driven security architecture.
