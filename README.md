## 📦 Automatisierter Versand von Schadensfotos an VTL-Portal

Dieses VBScript-Projekt automatisiert den Export und die Übertragung von Schadensfotos (z. B. beschädigte Packstücke) aus dem internen Speditionssystem an das [VTL-Portal](https://my.vtl.de/portal).

### 🔍 Hintergrund

Bereits im Jahr **2021** entstand die Anforderung, beschädigte Sendungen mit Fotodokumentation an das Kundenportal der VTL zu übermitteln. Zunächst erfolgte dieser Prozess **manuell**: Bilder mussten per Hand gespeichert, komprimiert und als XML-base64-Datei hochgeladen werden – ein fehleranfälliger und zeitaufwändiger Ablauf.

### ⚙️ Umsetzung

Im Rahmen dieser Lösung wurde der gesamte Ablauf automatisiert:

* 📤 **Datenbankabfrage**: Auswahl relevanter Fotos aus dem SQL-System (`V_Schaden_VTL_941`).
* 🖼️ **Speichern & Optimieren**: BLOBs werden als JPGs abgespeichert und mit ImageMagick (`magick.exe`) komprimiert.
* 🧾 **XML-Erstellung**: Automatische Generierung von VTL-konformen XML-Dateien mit Base64-kodierten Bilddaten.
* 🔄 **Statusupdate in SQL**: Markierung der exportierten Bilder.
* 📁 **Backup & Logging**: Versionssicherung und strukturierte Logdateien.
* 🌐 **Optionaler FTP-Upload**: Unterstützung für automatisierten Upload an FTP-Ziel (z. B. zur Weiterverarbeitung durch VTL-Partner).

### 🔐 Sicherheit

* Verbindungsdaten und Zugangsinformationen (SQL, FTP etc.) werden über eine zentrale verschlüsselte Konfigurationsdatei `key.zip` eingelesen.
* Arbeitsstatus wird über `.flag`-Dateien gesteuert, um parallele Ausführungen zu verhindern.

### ✅ Ergebnis

Diese Lösung hat seit 2021 den manuellen Aufwand bei der Bearbeitung von Transportschäden deutlich reduziert und sorgt für einen zuverlässigen, dokumentierten Datenfluss an das VTL-Portal.
