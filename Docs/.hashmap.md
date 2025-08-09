Here’s a complete `Hashmap.md` ready to drop into your `Docs/` directory. It explains the format, purpose, generation method, and includes both a sample entry and a wrapper snippet for automation:

---

# 🧭 `.hashmap` — Recon-Suite’s Audit Ledger

## 📌 Purpose

`.hashmap` is the traceability backbone of Recon-Suite. It links every scan, config, and input file to a unique hash and timestamp, ensuring:

- ✅ **Auditability**: You can prove what was scanned, when, and with what settings  
- 🔒 **Integrity**: You can verify that results haven’t been altered  
- 🧠 **Client Empowerment**: Clients can trace findings back to their own inputs  

---

## 🧬 Format

Each `.hashmap` entry is a YAML block with the following fields:

```yaml
report_id: 2025-08-09-001
tool: rusthound
target: dc01.internal.local
input_file: users.txt
input_hash: a3c9f1e2...
config_file: rusthound.conf
config_hash: 9b7d2c4a...
output_file: rusthound-output.json
output_hash: 2f8d7e1b...
timestamp: 2025-08-09T14:22:00Z
```

---

## 🧪 Sample Entry with Commentary

```yaml
report_id: 2025-08-09-002
tool: nmap
target: 192.168.1.1
input_file: targets.txt         # List of IPs scanned
input_hash: 7f3c1a...           # SHA256 of targets.txt
config_file: nmap-fast.conf     # Scan flags and exclusions
config_hash: 1a9b2e...          # SHA256 of config
output_file: nmap-output.xml    # Raw scan results
output_hash: 4c2d8f...          # SHA256 of output
timestamp: 2025-08-09T15:01:00Z # UTC timestamp
```

> Every hash is generated using SHA256. This ensures consistency and compatibility with most compliance frameworks.

---

## 🔧 Wrapper Snippet — Auto-Generate `.hashmap`

Here’s a Bash snippet to include in your tool wrappers:

```bash
#!/bin/bash
tool="nmap"
target="$1"
input_file="targets.txt"
config_file="nmap-fast.conf"
output_file="nmap-output.xml"
timestamp=$(date -u +"%Y-%m-%dT%H:%M:%SZ")

input_hash=$(sha256sum "$input_file" | awk '{print $1}')
config_hash=$(sha256sum "$config_file" | awk '{print $1}')
output_hash=$(sha256sum "$output_file" | awk '{print $1}')

cat <<EOF >> .hashmap
report_id: $(date -u +"%Y%m%d-%H%M%S")
tool: $tool
target: $target
input_file: $input_file
input_hash: $input_hash
config_file: $config_file
config_hash: $config_hash
output_file: $output_file
output_hash: $output_hash
timestamp: $timestamp
EOF
```

> You can modularize this into `generate_hashmap.sh` and source it from each tool wrapper.

---

## 📁 Location

`.hashmap` lives at the root of each scan session directory. It is never overwritten—each entry is appended chronologically.
