# SBOM

## Introduction

SBOM (Software Bill of Materials) is no longer a peripheral security topic. As systems grow more complex and rely heavily on open source and third-party artifacts, maintaining security without structural visibility becomes impractical. An SBOM provides that formalized visibility layer.

An SBOM is not just a dependency list. It is a structured document that describes the composition of a software artifact, with enough metadata to uniquely identify each component. This typically includes name, version, license, supplier, cryptographic hashes, dependency relationships, and ideally standardized identifiers such as PURL (Package URL) or CPE.

Conceptually, an SBOM can be modeled as a directed graph of components, where nodes are packages and edges represent dependency relationships. This enables automated reasoning about impact, risk inheritance, and transitive analysis.

The two dominant formats are SPDX and CycloneDX. SPDX originated in license compliance, while CycloneDX was designed with a stronger focus on application security. Both now support complex dependency modeling, hierarchical relations, digital signatures, and vulnerability data extensions.

## SBOM in Quor

In Quor, every published image includes its SBOM. You can access and download it in the UI:

1. Open the image catalog.
2. Select the desired image.
3. On the details page, open the **SBOM** tab.
4. Choose the version and architecture.
5. Download the complete SBOM.

SBOMs are generated at build time and published as security artifacts alongside signatures and provenance metadata. This provides a consistent, verifiable inventory across the image lifecycle.

## Why SBOM is structural to security

The core reason SBOM became critical is the asymmetry between consumption and control. Organizations consume thousands of dependencies with limited governance. When an incident like Log4Shell happens, the real question is not "do we have a scanner?" but "do we know exactly where this library is used?".

Without an SBOM, the answer depends on manual searches or rebuilding. With an SBOM, the organization has a verifiable inventory that can be correlated with vulnerability feeds like NVD, OSV, and GHSA. This reduces noise, improves traceability, and enables continuous reprocessing without rebuilding the artifact.

In mature environments, SBOMs are generated at build time and stored as versioned artifacts. As vulnerability databases update, the inventory can be re-evaluated without recompiling software, aligning with DevSecOps practices.
