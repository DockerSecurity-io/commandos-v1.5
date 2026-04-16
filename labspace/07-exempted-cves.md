# Commando 6. The Exempted CVEs

**Mission**: Mina returns from her patrol and tells Gord, "I found a few remaining CVEs, but they are not dangerous. We can let them be."

![Mina finds a depressed CVE](images/asgard-useless.png)

**Real-world context**: Not all CVEs are exploitable in your specific context. VEX (Vulnerability Exploitability eXchange) allows you to mark CVEs as not applicable to reduce alert noise and focus on real threats.

### Usage

Create a VEX statement:

```bash
vexctl create \
  --author="your-email@example.com" \
  --product="pkg:docker/flask-hello@latest" \
  --subcomponents="pkg:deb/debian/tar@1.35+dfsg-3.1" \
  --vuln="CVE-2025-45582" \
  --status="not_affected" \
  --justification="vulnerable_code_not_in_execute_path" \
  --file="CVE-2025-45582.vex.json"
```

Apply the VEX statement to Scout scan:

```bash
mkdir vex-statements
mv CVE-2025-45582.vex.json vex-statements/

docker scout cves flask-hello --vex-location ./vex-statements
```

### Exercises

- 6.1. Identify a CVE in your application that's not exploitable and create a proper VEX statement.
- 6.2. Research VEX justification categories and determine which applies to your use case.
