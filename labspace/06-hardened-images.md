# Commando 5. Docker Hardened Images

**Mission**: The Commandos reach the golden gates of a heavily fortified district. Thor says, "This district is heavily fortified, no CVE can get in here." The district is guarded by Hardened Warriors led by **Artemisia**, who says "I know how to recognize CVEs, I will join you."

![Hardened Images](images/asgard-4.png)

**Real-world context**: Docker Hardened Images (DHI) are near-zero-CVE base images maintained by Docker, providing a more secure foundation with dramatically reduced attack surface.

### Usage

Build an application with hardened base:

```dockerfile
# Non-hardened Node image
FROM node:25

# Hardened Node image for development
FROM dhi.io/node:25-dev AS build

# Hardened Node image for production
FROM dhi.io/node:25
```

Compare standard vs hardened Node images:

```bash
# Standard Node image
docker scout cves node:25

# Hardened Node image
docker scout cves dhi.io/node:25
```

### Exercises

- 5.1. Audit your current base image usage and calculate CVE reduction potential with hardened images.
- 5.2. Build the same application with standard and hardened base images, compare Scout results.
