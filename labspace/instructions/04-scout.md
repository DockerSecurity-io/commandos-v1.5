# Commando 3. Scout

**Mission**: Gord orders Jack, Agent Null, and Mina to scout the remaining districts of Asgard for hidden CVEs. "Let's hunt some CVEs!" says Null.

![Scout hunting for CVEs](images/asgard-3.png)

**Real-world context**: Docker Scout analyzes your images for vulnerabilities by cross-referencing the SBOM with CVE databases, providing actionable security intelligence.

### Usage

To check the vulnerabilities in the image, run:

```bash
docker scout cves flask-server:latest
```

You can also check the vulnerabilities using the Docker Desktop UI. Just go to the "Images" tab, select the image, and click on "Scout".

Try comparing base images for security:

```bash
# Standard Node image
docker scout cves node:20

# Alpine Node image
docker scout cves node:20-alpine

# Which is more secure?
```

### Exercises

- 3.1. Build an application with an old base image (e.g., `node:14`) and compare Scout results with newer versions.
- 3.2. Use the `--details` flag to get more information about specific vulnerabilities.
