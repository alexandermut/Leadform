# 🗺️ Roadmap: Lead Erfassungs App

Diese Roadmap dokumentiert den aktuellen Entwicklungsstand, geplante Optimierungen und zukünftige Erweiterungsmöglichkeiten für die Leasing & Factoring Lead-App.

---

## ✅ Phase 1: MVP & Core Stability (Abgeschlossen)
**Ziel:** Eine funktionierende, offline-fähige App für den Messe-Einsatz ohne Backend-Abhängigkeit.

*   **Architektur:**
    *   [x] Single Page Application (Vanilla JS, HTML5, CSS3).
    *   [x] Vollständiger Verzicht auf externe Frameworks/Bibliotheken.
    *   [x] Dark Mode Design (OLED-freundlich & Batteriesparend).
*   **Lead-Erfassung:**
    *   [x] Felder für Leasing/Factoring (Investitionsvolumen, Zeithorizont, Interessen-Dropdown).
    *   [x] Automatische Währungsformatierung (10.000,00 €).
    *   [x] Visitenkarten-Fotoaufnahme (Kamera-Integration).
*   **E-Mail-Workflow:**
    *   [x] `mailto:`-Generierung mit RFC-konformen Zeilenumbrüchen (`\r\n`).
    *   [x] Intelligenter Workaround für Foto-Anhang: **Auto-Copy to Clipboard** beim Senden.
    *   [x] Dynamischer Betreff & Body.
    *   [x] CC-Steuerung für Kunden (Standard: An).
*   **Daten-Persistenz (LocalStorage):**
    *   [x] Speicherung der internen E-Mail-Adressen (Vertrieb/Assistenz).
    *   [x] Speicherung der Toggle-Zustände für "Teilweise Leeren".
*   **UX / UI:**
    *   [x] Mobile-First Layout mit Sticky-Footer.
    *   [x] iOS-Optimierungen (Kein Zoom bei Fokus, Nummern-Tastatur).
    *   [x] Apple-Style Toggles & Glassmorphismus.

---

## 🚀 Phase 2: UX Polish & PWA (Nächste Schritte)
**Ziel:** Die App soll sich wie eine native App anfühlen und installationsfähig werden.

*   **Progressive Web App (PWA):**
    *   [ ] `manifest.json` erstellen (App Icon, Name, Standalone-Modus).
    *   [ ] Service Worker implementieren (Offline-Caching der Assets `index.html`, `style.css`, `script.js` für garantierte Verfügbarkeit auch im Flugmodus).
    *   [ ] "Add to Homescreen" Prompt Logik.
*   **Foto-Handling Optimierung:**
    *   [ ] Komprimierung des Fotos vor dem Clipboard-Copy (Performance auf älteren Geräten).
    *   [ ] Optional: OCR (Texterkennung) via Tesseract.js (würde App-Größe erhöhen, aber Abtippen ersparen).
*   **Komfort-Funktionen:**
    *   [ ] "Rückgängig"-Funktion (Undo) nach dem Löschen (für 5 Sekunden).
    *   [ ] Vibrations-Feedback (Haptic API) bei Erfolg/Fehler.

---

## 📊 Phase 3: Daten-Sicherheit & Export (Mittelfristig)
**Ziel:** Sicherheit gegen Datenverlust, falls die E-Mail-App abstürzt.

*   **Lokaler Notfall-Speicher:**
    *   [ ] Speichern der letzten 10 Leads im `localStorage` als Backup ("Gesendete Leads Historie").
    *   [ ] Möglichkeit, einen Lead aus der Historie wiederherzustellen.
*   **CSV / Excel Export:**
    *   [ ] Funktion "Tagesabschluss": Exportiert alle lokal gespeicherten Leads des Tages als `.csv` Datei zum Download.
    *   [ ] Button "Liste löschen" für den nächsten Tag.
*   **Validierung:**
    *   [ ] Prüfung auf Dubletten (Warnung, wenn E-Mail bereits heute erfasst wurde).

---

## ☁️ Phase 4: Backend Integration (Langfristig / Optional)
**Ziel:** Automatisierung und CRM-Anbindung (verlässt den reinen Offline-Ansatz).

*   **Server-Side Sending:**
    *   [ ] API-Endpunkt zum direkten Versenden (statt `mailto`).
    *   [ ] Echte Dateianhänge für Fotos.
*   **CRM-Anbindung:**
    *   [ ] Direkter Push in Salesforce / HubSpot / Pipedrive via Webhook.
*   **Authentifizierung:**
    *   [ ] Login für Vertriebsmitarbeiter.

---

## ⚠️ Bekannte Limitierungen & Workarounds

| Limitierung | Status | Workaround |
| :--- | :--- | :--- |
| **Keine Foto-Anhänge** | Systembedingt | Das Foto wird in die Zwischenablage kopiert. Der Nutzer muss es manuell in die Mail einfügen. |
| **Kein Server** | Gewollt | Alle Daten liegen nur auf dem Gerät des Nutzers. Datenschutzfreundlich, aber kein zentrales Backup. |
| **iOS Safari Zoom** | Gelöst | `font-size: 1.2rem` verhindert Auto-Zoom beim Tippen. |
| **Gmail Formatierung** | Gelöst | Nutzung von `\r\n` erzwingt korrekte Zeilenumbrüche auch in der Gmail iOS App. |
