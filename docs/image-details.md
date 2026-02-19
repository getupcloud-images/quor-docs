# Image Details

The Image Details page centralizes everything you need to understand, use, and verify a container image. Each tab focuses on a specific aspect of the image.

## Versions

Shows available tags for the image, their last update dates, and the pull command for each tag (when the user is subscribed). This is where you choose the version you want to use and grab the exact `docker pull` command.

## SBOM

Lists every component included in the image and the license for each package. You can filter by image version and architecture, browse the full component list, and download the SBOM file for compliance or auditing.

## Provenance

Explains signed attestations that prove how the image was built and what metadata is attached. It provides:

- A command to verify the image signature using `cosign` (and `jq`).
- A list of available attestations: SLSA provenance, CycloneDX SBOM, SPDX SBOM, and VEX.
- Commands to retrieve a specific attestation by predicate type and platform.
- A command to verify attestations using the predicate type URI.
