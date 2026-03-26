# VEX

## Introduction

VEX (Vulnerability Exploitability eXchange) adds exploitability context to CVE findings.
It complements scanner output by stating whether a vulnerability is relevant for a specific image version.

## VEX and SBOM

- **SBOM** answers what is inside the image.
- **VEX** answers if reported CVEs are exploitable in that context.

## Status model

Quor follows the standard VEX status model:

- `not_affected`
- `affected`
- `fixed`
- `under_investigation`

## VEX in Quor

For all Quor images and versions, VEX is published with the image evidence set, together with:

- SBOM
- Signature
- Provenance attestations

## Practical impact on CI/CD

Using VEX helps reduce vulnerability triage noise and prioritize real risk in CI/CD pipelines.
