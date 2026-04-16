# Commando 8. Docker Bake

**Mission**: As the Commandos defeated the CVEs in Asgard, they decided to throw a party to celebrate their victory, and discuss the security measures they can implement systematically.

![The Commandos celebrate their victory](images/asgard-5.png)

**Real-world context**: Docker Bake allows you to define complex build configurations in files, making security practices repeatable, reviewable, and automated across your entire organization.

### Usage

Examine the `docker-bake.hcl` file:

```hcl
target "default" {
  context = "."
  dockerfile = "Dockerfile"
  tags = ["flask-hello:latest"]

  attest = [
    {
      type = "sbom"
    }
  ]
}
```

Run the build with Bake:

```bash
docker buildx bake
```

### Exercises

- 8.1. Add provenance attestations to the bake file.
- 8.2. Add multi-platform builds (linux/amd64, linux/arm64).
