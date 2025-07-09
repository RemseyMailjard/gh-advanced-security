# 🔐 Oefening: Custom Secret Scanning in GitHub Advanced Security

In deze oefening leer je hoe je je **eigen geheime tokens** kunt detecteren met behulp van **custom secret scanning patterns** in GitHub Advanced Security (GHAS).



## 🌟 Doel van deze oefening

Aan het einde van deze oefening kun je:

- Een eigen **regex-patroon** definiëren voor secret scanning
- Het patroon implementeren in een repository
- Een GitHub **alert triggeren** op basis van je eigen patroon

---

## 🧰 Wat heb je nodig?

- Een GitHub repository waar **GitHub Advanced Security** is ingeschakeld (of een oefenrepo van de trainer)
- Rechten om bestanden toe te voegen en instellingen te wijzigen
- Basiskennis van Git en GitHub

---

## 🛋️ Stap 1: Voeg een geheim toe aan je repo

1. Maak een nieuw bestand aan:

   ```
   src/config.py
   ```

2. Voeg daarin de volgende (fictieve) API-key toe:

   ```python
   API_KEY = "sk_demo_1234567890abcdef1234567890abcdef"
   ```

3. Commit en push dit bestand naar GitHub.

> ⚠️ Let op: gebruik **nooit echte API-sleutels** voor deze oefening!

---

## 🧐 Stap 2: Definieer je eigen secret pattern

1. Maak de volgende mapstructuur aan in je repo:

   ```
   .github/secret-scanning/custom-patterns/
   ```

2. Voeg in deze map een JSON-bestand toe met de naam:

   ```
   fake-token.json
   ```

3. Plak de volgende JSON-inhoud in het bestand:

   ```json
   {
     "name": "Fake API Key",
     "pattern": "sk_demo_[0-9a-fA-F]{32}",
     "secretGroup": "demo_api_key"
   }
   ```

> 🧪 Dit patroon herkent tokens die beginnen met `sk_demo_` gevolgd door 32 hexadecimale tekens.

---

## ⚙️ Stap 3: Activeer GitHub Advanced Security

1. Ga in GitHub naar je repository
2. Klik op `Settings > Code security and analysis`
3. Zet de volgende opties **aan**:
   - ✅ Enable GitHub Advanced Security
   - ✅ Enable secret scanning
   - ✅ Enable custom patterns

---

## 🚀 Stap 4: Trigger een secret scan

1. Zorg ervoor dat je alles hebt gepusht:
   - Het `config.py` bestand met de geheime sleutel
   - Het `fake-token.json` bestand met je patroon
2. Wacht een paar minuten of voer een extra commit uit
3. Ga naar **Security > Secret scanning alerts** in je repo

---

## ✅ Wat je geleerd hebt

- Hoe je een custom secret scanning pattern definieert in JSON
- Hoe je GHAS gebruikt om je eigen tokens op te sporen
- Hoe GitHub je helpt met automatische beveiligingscontroles

---

## 🧠 Bonus: uitbreiden

- Pas het patroon aan zodat het ook `sk_test_` tokens herkent
- Voeg meerdere patronen toe in aparte JSON-bestanden
- Test het ook met andere bestandstypen zoals `.env` of `.json`

---

## 📸 Laat zien wat je hebt gedaan

Heb je een alert gekregen? Super!\
➡️ Maak een screenshot van je alert in GitHub en deel deze in de groep.


Veel succes en veel plezier met veilig ontwikkelen! 💪[

