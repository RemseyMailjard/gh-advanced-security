# gh-advanved-security
Repository for GitHub Advanced Security Hands-On

# 🧪 GitHub Advanced Security – Hands-on Oefeningen

Welkom bij de praktische oefeningen rond GitHub Advanced Security. Deze repo bevat kwetsbare demo-code die je kunt gebruiken om te leren werken met de belangrijkste beveiligingsfeatures van GitHub.

---

## ✅ 1. Code Scanning – Kwetsbaarheden vinden met CodeQL
📁 Bestand: `code-scanning/app.py`

🔧 **Opdracht:**
1. Push deze directory naar je eigen GitHub-repo.
2. Activeer **CodeQL Analysis** via **Security > Code scanning alerts > Set up CodeQL**.
3. Laat GitHub de workflow uitvoeren.

📌 **Vraag:**
- Welke 3 kwetsbaarheden herkent GitHub in dit script?

💡 **Tip:**
- Gebruik “View alert” om meer uitleg te krijgen over elke kwetsbaarheid.

---

## ✅ 2. Secret Scanning – Gevoelige gegevens detecteren
📁 Bestand: `secret-scanning/alertmanager.yaml`

🔧 **Opdracht:**
1. Zorg dat dit bestand in een repository staat.
2. Activeer “Secret scanning” (meestal standaard actief).

📌 **Vraag:**
- Wordt de Slack webhook gedetecteerd als geheim?
- Waarom is dit gevaarlijk?

💡 **Extra:**
- Voeg een nep-API key toe aan een `.env` bestand en commit dit. Wat gebeurt er?

---

## ✅ 3. Dependency Review – Kwetsbare packages spotten
📁 Bestanden: `dependabot/app.py` + `dependabot/requirements.txt`

🔧 **Opdracht:**
1. Push deze map naar een aparte branch.
2. Open een Pull Request.
3. Bekijk het tabblad **Security > Dependency graph > Dependency review**.

📌 **Vraag:**
- Welke afhankelijkheden hebben bekende kwetsbaarheden?

💡 **Extra:**
- Activeer Dependabot alerts in de repo-instellingen.

---

## ✅ 4. Dependabot configureren – Automatisch kwetsbaarheden opsporen
📂 Doelmap: `.github/`  
📄 Bestand: `dependabot.yml`

🔧 **Opdracht:**
1. Maak in je repo de map `.github` aan (indien nog niet aanwezig).
2. Voeg het bestand `dependabot.yml` toe met deze inhoud:

```yaml
# .github/dependabot.yml
version: 2
updates:
  - package-ecosystem: "pip"
    directory: "/dependabot"  # pad naar requirements.txt
    schedule:
      interval: "weekly"
    open-pull-requests-limit: 5
    allow:
      - dependency-type: "all"

