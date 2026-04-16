# Commando 4. SBOM Attestations

**Mission**: The Valkyrie sets up a camera with face recognition and says, "I can generate an ID card for everyone in Asgard, and attach it to their database face record. That way, we can verify their identity at the checkpoints."

![SBOM Attestations](images/asgard-3.1.png)

**Real-world context**: SBOM attestations are SBOMs generated during build time and cryptographically signed, providing tamper-proof component information that travels with your image.

### Usage

SBOM attestations are generated during the build:

```bash
docker buildx build --sbom=true -t cpp-hello:with-sbom .
```

Now, let's check the CVEs with Docker Scout:

```bash
docker scout cves cpp-hello:with-sbom
```

It will say:

```
SBOM obtained from attestation, 0 packages found
```

To include the build stage packages in the SBOM, add the following line to the beginning of the `Dockerfile`:

```dockerfile
ARG BUILDKIT_SBOM_SCAN_STAGE=true
```

Now, rebuild the image:

```bash
docker buildx build --sbom=true -t cpp-hello:with-build-stage .
```

Check the SBOM attestations for the image again:

```bash
docker scout cves cpp-hello:with-build-stage
```

### Exercises

- 4.1. Store the SBOM locally: `docker buildx build --sbom=true --sbom-output=type=local,dest=. -t test-image .`
- 4.2. Compare SBOM results with and without `BUILDKIT_SBOM_SCAN_STAGE=true` for a multi-stage build.
