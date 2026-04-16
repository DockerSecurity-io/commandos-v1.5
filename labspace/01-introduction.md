# 🛡 The 10 Docker Commandos: Asgard Mission

Welcome to the **Docker Commandos** workshop. In this mission, you will join an elite team of security specialists to defend Asgard from a shadow monster outbreak known as CVEs.

![Docker Commandos](images/commandos-v5.png)

## Meet your team:

- **Agent Null** 🎭 - The masked hunter
- **Wilhelmina (Mina)** 🧛‍♀️ - The undead assassin
- **Gord** ⚔️ - The swordmaster
- **Rothütle** 🎩 - The tactician
- **Captain Ahab** 🐋 - The veteran commander
- **The Valkyrie** 🛡️ - The identity specialist
- **Jack** 🤖 - The cyborg soldier
- **Evie** 🤠 - The sharpshooter

## Prologue: The Attack on Asgard

Thor enters Odin's chamber hastily, "Father, Asgard is under attack! Shadow monsters called CVEs are in Asgard and my hammer Mjolnir can't destroy them!" Odin looks at him calmly, "**Summon the Docker Commandos**!"

![Docker Commandos arrive at Asgard](images/asgard-1.png)

## Command Dependencies

```mermaid
flowchart TD
    A[Docker Init] --> B[SBOM Generation]
    B --> C[Scout CVE Analysis]
    C --> D[SBOM Attestations]
    C --> E[Hardened Images]
    C --> F[VEX Exemptions]
    D --> G[VEX Attestations]
    F --> G
    E --> H[Docker Bake]
    G --> H
    H --> J[Cosign]
    J --> I[Zero-Day Defense]

    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#fff3e0
    style D fill:#e8f5e8
    style E fill:#fce4ec
    style F fill:#fff8e1
    style G fill:#f1f8e9
    style H fill:#e3f2fd
    style J fill:#e8eaf6
    style I fill:#ffebee
```
