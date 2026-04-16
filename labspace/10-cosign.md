# Commando 9. Cosign

**Mission**: With the party still going, Evie steps away from the celebration and quietly gets to work. One by one, she signs each SBOM attestation and each VEX attestation with her special pen, ensuring their originality. "A document without a signature is just a rumor," she says.

**Real-world context**: Cosign (part of the Sigstore project) lets you cryptographically sign container images and attestations. Consumers can then verify those signatures before running anything.

### Usage

Generate a key pair:

```bash
cosign generate-key-pair
```

Sign the image:

```bash
cosign sign --key cosign.key your-image:latest
```

Verify the signature:

```bash
cosign verify --key cosign.pub your-image:latest
```

### Exercises

- 9.1. Sign an image and its SBOM attestation.
- 9.2. Research keyless signing with Sigstore.
