# 🛰️ Github Actions For Bug Bounty

Automate your reconnaissance and vulnerability scanning with **GitHub Actions**.  
This repository provides two powerful CI/CD workflows:

- **Subdomain Monitor** — Continuously track domain changes with [Subfinder](https://github.com/projectdiscovery/subfinder) and get Discord notifications when new or removed subdomains are detected.  
- **Vulnerability Scanner** — Run [Nuclei](https://github.com/projectdiscovery/nuclei) on discovered subdomains to identify security issues, automatically reporting results to Discord.

---

## 🚀 Features

### 🧭 Subdomain Monitor
- Runs every 6 hours (configurable via cron).
- Automatically detects new and removed subdomains.
- Generates detailed Discord embed notifications.
- Stores previous results in the repository for historical comparison.
- Automatically commits updated subdomain lists.

### 🧨 Vulnerability Scanner
- Performs scheduled or manual domain scans.
- Uses **Subfinder** for subdomain enumeration.
- Uses **Nuclei** to detect **critical, high, and medium** vulnerabilities.
- Sends detailed vulnerability findings to Discord (one per message).
- Uploads scan artifacts (`subdomains.txt`, `nuclei-results.txt`) to GitHub Actions.

---

## 🛠️ Requirements

- GitHub repository with Actions enabled.
- Go 1.21+ installed via workflow.
- Secrets configured:
  ```yaml
  DISCORD_WEBHOOK: <your_discord_webhook_url>
  ```

---

## ⚙️ Setup

1. Copy the workflow files to your repository:
   ```
   .github/workflows/SubdomainMonitor.yaml
   .github/workflows/VulnScan.yaml
   ```

2. Configure the Discord webhook in your repo’s secrets:
   - Go to **Settings → Secrets and variables → Actions → New repository secret**
   - Add:
     ```
     Name: DISCORD_WEBHOOK
     Value: https://discord.com/api/webhooks/your_webhook_id
     ```

3. (Optional) Adjust the cron schedule:
   - In `SubdomainMonitor.yaml`, modify:
     ```yaml
     - cron: '0 */6 * * *' # Every 6 hours
     ```
   - In `VulnScan.yaml`, modify:
     ```yaml
     - cron: '0 6 * * 1' # Every Monday at 6 AM UTC
     ```

---

## 🔧 Manual Execution

You can trigger either workflow manually from GitHub Actions:
- Go to the **Actions** tab.
- Choose the workflow (e.g., *Subdomain & Vulnerability Scanner*).
- Click **Run workflow** and enter a domain (e.g., `example.com`).

---

## 📊 Example Discord Notifications

**Subdomain Monitor Embed:**
```
Subdomain Report for example.com
Current Subdomains: 42
New Subdomains: 3
Removed Subdomains: 1
```

**Vulnerability Alerts:**
```
🚨 Vulnerability Found
Domain: example.com
[medium] Exposed config.json – https://sub.example.com/config.json
```

---

## 🧩 Tools Used

| Tool | Description |
|------|--------------|
| [Subfinder](https://github.com/projectdiscovery/subfinder) | Subdomain enumeration tool |
| [Nuclei](https://github.com/projectdiscovery/nuclei) | Template-based vulnerability scanner |
| [jq](https://stedolan.github.io/jq/) | JSON processor used for formatting Discord messages |

---

## 📦 Artifacts

After each run, GitHub Actions will upload:
- `subdomains.txt`
- `nuclei-results.txt`

You can download these under the **Artifacts** section of the workflow run.

---

## 🧠 Roadmap
- Add support for HTTPx for live host verification.
- Integrate CVE severity scoring in Discord notifications.
- Add automatic PR generation for newly detected high-severity vulnerabilities.

---

## 🏁 License
This project is open source under the [MIT License](LICENSE).
