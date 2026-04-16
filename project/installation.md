
# Pre‑Workshop Installation Guide: Docker Commandos v1.5 — Asgard Mission

> **All shell commands assume a Unix-based terminal (bash/zsh). If you are on Windows, install [Git Bash](https://git-scm.com/downloads) and run all commands from it.**

---

## 0. Install Docker Desktop

- **Download and install** Docker Desktop for your OS (version **4.63 or later** recommended).
- **To switch context after installation**, open your terminal and run:
  ```bash
  docker context ls
  docker context use desktop-linux
  ```
  Replace `desktop-linux` with the appropriate context name for your OS.

---

## 1. Clone the Repository

```bash
git clone https://github.com/DockerSecurity-io/commandos-v1.5
cd commandos-v1.5
```

---

## 2. Install the Following Command-Line Tools

| Tool | Purpose | Install |
|------|---------|---------|
| `vexctl` | Create and manage VEX statements | [github.com/openvex/vexctl/releases](https://github.com/openvex/vexctl/releases) |
| `oras` | Inspect OCI referrers (SBOMs, VEX, provenance) | [oras.land/docs/installation](https://oras.land/docs/installation) |
| `trivy` | Alternative container image CVE scanner | [aquasecurity.github.io/trivy](https://aquasecurity.github.io/trivy/latest/getting-started/installation/) |
| `cosign` | Sign and verify container images and attestations | `brew install cosign` (Mac) / [docs.sigstore.dev/cosign/system_config/installation](https://docs.sigstore.dev/cosign/system_config/installation/) (Windows) |
| `jq` | JSON processing (used in DHI login script) | `brew install jq` (Mac) / [stedolan.github.io/jq](https://stedolan.github.io/jq/download/) (Windows) |


Check the installation with:

```bash
make check
```

---

## 3. Log In to Docker Hub and DHI

You need a Docker Hub account to push images in Commando 7.

```bash
docker login
```

For **Docker Hardened Images (DHI)**, log in to `dhi.io` using your Docker Desktop credentials:

```bash
echo index.docker.io | docker-credential-desktop get | jq -r '"-u \(.Username) --password-stdin"' | xargs -I {} sh -c 'echo $(echo index.docker.io | docker-credential-desktop get | jq -r .Secret) | docker login dhi.io {}'
```

> **Note**: Use your Rabobank business Docker Hub account when prompted.

---

## 4. Pre-Pull Images

To avoid slow downloads during the workshop, pull all required images in advance:

```bash
make pull
```

---

## 5. Command Availability Reference

| Command | Status | Free / Paid | Desktop Version | Notes |
|---------|--------|-------------|-----------------|-------|
| **docker init** | GA | Free (Desktop only) | 4.27+ | Included in Docker Desktop. |
| **docker buildx bake** | GA | Free / Open-source | 4.45+ | Included in Docker Desktop. |
| **docker sbom** | Plugin | Free / Open-source | Included | Included in Docker Desktop. |
| **SBOM attestation** (`buildx --sbom`) | GA | Free / Open-source | Post-2023 | Use `docker buildx build --sbom=true`. |
| **docker scout** | GA | Free tier | 4.17+ | Included in Docker Desktop. |
| **docker debug** | GA | Pro/Team/Business | 4.33+ | Included in Docker Desktop. |

---

## Summary

- Install **Docker Desktop 4.63+** — it includes all required Docker features out of the box.
- **Windows users**: install **Git Bash** and run all commands from it.
- Run `make check` to verify all tools are installed, and `make pull` to pre-pull all images.
- Make sure you can log in to both **Docker Hub** and **dhi.io** before arriving.
