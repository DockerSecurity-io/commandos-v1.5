# Docker Commandos Labspace

This directory contains the content and configuration for the **Docker Commandos: Asgard Mission** labspace. This labspace is designed to be run in interactive environments similar to Killercoda or Docker's Labspace platform.

## Structure

- `labspace.yaml`: The main configuration file defining the metadata, title, and sequence of sections.
- `*.md`: Markdown files for each section of the lab, following the Docker Commandos storyline.
- `images/`: Visual assets used throughout the lab, including mission artwork and character portraits.

## Running Locally

To preview or run this labspace locally, you can use the `labspace` CLI or Docker Compose with the provided `compose.yaml`.

### Using Docker Compose

The `compose.yaml` in this directory uses the official Docker Labspace base. A `.env` file is provided to set the `CONTENT_PATH`.

Run it from this directory:

```bash
docker compose up -d
```

Then, open your browser at `http://localhost:3030`.

### Using OCI Artifacts (Future)

Once this labspace is published to an OCI registry, it can be launched directly without cloning:

```bash
docker compose -f oci://<your-registry>/docker-commandos-labspace up -d
```

## Content Overview

The lab walks through 10 security "Commandos":
1. **Docker Init**: Secure project initialization.
2. **SBOM**: Software Bill of Materials.
3. **Scout**: Vulnerability scanning.
4. **SBOM Attestations**: Build-time metadata.
5. **Hardened Images**: Using `dhi.io`.
6. **Exempted CVEs**: VEX statements.
7. **VEX Attestation**: Signed exemptions.
8. **Docker Bake**: Complex build automation.
9. **Cosign**: Cryptographic signing.
0. **Zero-Day**: Defense-in-depth.

## Assets

Images are sourced from the `dockersecurity.io` repository and include:
- Mission-specific artwork (`asgard-*.png`)
- Team portraits (`po-*.png`)
- Team posters (`commandos-v5.png`)
