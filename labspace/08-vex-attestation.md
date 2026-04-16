# Commando 7. VEX Attestation

**Mission**: The Valkyrie issues "Check Exemption" badges for the Exempted CVEs, and adds them to the checkpoints. "The Exempted CVEs can pass through the checkpoints without being flagged, as they are not a threat to us."

![Mina found a new warrior when fighting CVEs](images/asgard-4.5.png)

**Real-world context**: VEX attestations are cryptographically signed exemptions that travel with your image, providing tamper-proof vulnerability exception documentation that's verified automatically.

### Usage

Add VEX attestation to image:

```bash
docker scout attestation add \
  --file exemption.vex.json \
  --predicate-type https://openvex.dev/ns/v0.2.0 \
  aerabi/flask-hello:with-sbom
```

Next time, you won't need to pass the VEX statement to the Scout scan, as it is already attached to the image:

```bash
docker scout cves aerabi/flask-hello:with-sbom
```

### Exercises

- 7.1. Research how else can one generate VEX statements besides using `vexctl create` command.
- 7.2. Explore the OCI referrers for a DHI image and identify the VEX attestation and its signature.
