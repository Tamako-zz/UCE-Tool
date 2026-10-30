# UCE Tool

[简体中文](README.zh-CN.md) | [English](README.en.md) | **Deutsch** | [日本語](README.ja.md) | [Français](README.fr.md)

UCE Tool ist die Desktop-Anwendung für USB-C Explorer. Sie zeigt Live-Messwerte, liest E-Marker-Daten, erkennt Ladeprotokolle, aktualisiert die Gerätefirmware und konfiguriert Gerätefarben.

Unterstützt werden Windows 64-Bit sowie Macs mit Apple Silicon und Intel. Die Oberfläche ist auf Chinesisch, Englisch, Deutsch, Japanisch und Französisch verfügbar.

**[Neueste Version herunterladen](https://github.com/Tamako-zz/UCE-Tool/releases/latest)** · **[Alle Versionen](https://github.com/Tamako-zz/UCE-Tool/releases)**

## Inhalt

- [Download und Installation](#download)
- [Gerät verbinden](#connect)
- [Dashboard und Live-Diagramm](#dashboard)
- [E-Marker und Protokoll](#emarker)
- [Ladeprotokolle und PDOs](#protocol)
- [Gerätefirmware aktualisieren](#firmware)
- [Gerätefarben konfigurieren](#theme)
- [Sprache, Darstellung und Geräteinformationen](#settings)
- [UCE Tool aktualisieren](#software-update)
- [Fehlerbehebung](#faq)

<a id="download"></a>
## Download und Installation

Auf der [Release-Seite](https://github.com/Tamako-zz/UCE-Tool/releases/latest) unter **Assets** die passende Datei auswählen:

| Datei | Plattform | Anwendung |
| --- | --- | --- |
| `UCE-Windows-x64.zip` | Windows 64-Bit, Intel / AMD | `UCE.exe` |
| `UCE-mac-arm64.dmg` | Mac mit Apple Silicon (M-Serie) | `UCE.app` |
| `UCE-mac-x86_64.dmg` | Mac mit Intel | `UCE.app` |

Den Mac-Prozessor finden Sie unter **Apple-Menü → Über diesen Mac**.

**Windows:** ZIP vollständig entpacken und `UCE.exe` aus dem entpackten Ordner starten.

**macOS:** Passende DMG öffnen, `UCE.app` nach **Applications** ziehen, das Abbild auswerfen und UCE aus „Programme“ öffnen. Blockiert macOS den ersten Start, prüfen Sie die Quelle und erlauben Sie das Öffnen unter **Systemeinstellungen → Datenschutz & Sicherheit**.

<a id="connect"></a>
## Gerät verbinden

Sie benötigen einen USB-C Explorer, ein datenfähiges USB-Kabel und zur Hardware passende APP-Firmware. Themen- und Protokollfunktionen benötigen ebenfalls kompatible Firmware.

1. UCE Tool starten und das Gerät über seine Datenschnittstelle verbinden.
2. Die Anwendung sucht Geräte und versucht automatisch eine Verbindung. Links muss **Verbunden** erscheinen.
3. Gewünschte Seite öffnen. Die Gerätekarte zeigt Name, abgekürzte Seriennummer und APP-Version; die vollständige Seriennummer steht in den Einstellungen.

Bei mehreren Geräten durch Anklicken der Gerätekarte wechseln. Während eines Updates warten, bis der Vorgang abgeschlossen ist. Im **BOOT-Modus** kann die APP per Firmware-Update wiederhergestellt werden; Live-Messungen benötigen laufende APP-Firmware.

<a id="dashboard"></a>
## Dashboard und Live-Diagramm

Gerät verbinden, **Dashboard** öffnen und das Startsymbol anklicken. Messwerte und Diagramm werden laufend aktualisiert.

| Kanal | Bedeutung |
| --- | --- |
| VBUS / IBUS / POWER | Spannung (V), Strom (A) und Leistung (W) |
| D+ / D− | Spannungen der USB-Datenleitungen |
| CC1 / CC2 | Spannungen der USB-C-CC-Pins |

Kanalschaltflächen zeigen oder verbergen Kurven. Spannung, Strom und Leistung haben eigene Skalen. Mit der Maus über dem Diagramm lassen sich Messpunkte anzeigen; `--` bedeutet, dass dort kein Messwert vorliegt.

Abtastraten: **1, 10 oder 50 SPS**; Zeitfenster: **10, 30, 60 oder 120 Sekunden**. Die Stopp-Schaltfläche pausiert die Erfassung; beim Fortsetzen zählt die Pausenzeit nicht mit. „Leeren“ entfernt den Verlauf und setzt die Zeit zurück; im pausierten Zustand muss anschließend erneut gestartet werden.

<a id="emarker"></a>
## E-Marker und Protokoll

Kabel am gekennzeichneten Anschluss anschließen, **E-Marker** öffnen und **Lesen** oder **Kontinuierlich lesen** wählen. Vor der kontinuierlichen Erkennung alle anderen Verbraucher vom Geräteausgang trennen. Dieselbe Schaltfläche beendet die kontinuierliche Erkennung.

Je nach Meldung zeigt die Seite Kabeltyp, Strom, maximale Spannung, USB-Geschwindigkeit, PD-Version, TBT, EPR und Länge/Latenz. Nicht gemeldete oder unbekannte Werte werden als „Unbekannt“ angezeigt. Wird kein E-Marker gefunden, Kabel und Anschluss prüfen. Die VDO-Rohdaten stehen unter der Grafik.

Erfolgreiche Lesungen erscheinen im Erkennungsprotokoll der aktuellen Sitzung. Der Export erstellt eine `.xlsx`-Datei mit Zeitstempeln, Kabelinformationen und VDOs. Die Zeitangaben verwenden UTC+8. Beim Beenden wird das Protokoll gelöscht; benötigte Daten vorher exportieren.

<a id="protocol"></a>
## Ladeprotokolle und PDOs

Ladegerät oder Quelle am gekennzeichneten Anschluss verbinden, **PD-Erkennung** öffnen und die Erkennung starten. Dabei kann die Spannung steigen: Vorher alle Verbraucher vom Ausgang trennen. Mit derselben Schaltfläche lässt sich die Erkennung stoppen.

Die Seite zeigt gemeldete PDO-Spannung, Strom und Leistung sowie die jeweiligen Zustände „Bestanden“, „Fehlgeschlagen“, „Ausstehend“ oder „Nicht unterstützt“. Die verfügbaren Tests hängen von der Gerätefirmware ab. Ist das Gerät beschäftigt, zuerst den laufenden Test beenden.

<a id="firmware"></a>
## Gerätefirmware aktualisieren

Diese Seite aktualisiert die Firmware **auf dem USB-C Explorer**.

1. Gerät verbinden und **Firmware-Update** öffnen.
2. **Versionen abrufen** anklicken.
3. Hinweise lesen und eine zur Hardware passende Version auswählen. Bei mehreren BIN-Dateien die passende Datei anhand der Versionshinweise wählen.
4. Auf der Versionskarte **Aktualisieren** anklicken. Die gewählte Firmware wird heruntergeladen, geprüft und übertragen. Fortschritt und Ergebnis stehen auf der Karte.

Nur die gewählte Firmware wird heruntergeladen; die temporäre Datei wird nach dem Vorgang bereinigt. USB während des Updates verbunden lassen und nicht das Gerät wechseln. Danach in den Einstellungen die Geräteinformationen aktualisieren und die APP-Version prüfen. Bei Fehlern Meldung aufbewahren, Verbindung und Kompatibilität prüfen und erneut versuchen.

<a id="theme"></a>
## Gerätefarben konfigurieren

**Themenkonfiguration** öffnen, mit den Pfeilen die Vorschauseite wechseln, bearbeitbare Farbfelder anklicken und den Hintergrund unter der Vorschau wählen. **Auf Gerät anwenden** zeigt die Farben sofort; **Auf Gerät speichern** erhält sie nach einem Neustart.

Die Vorschau umfasst Messungen, Statistik, E-Marker, Protokollerkennung und Geräteeinstellungen. Auf der Statistikseite sind Titel, MAX, CUR, Ah und Wh konfigurierbar; die Gerätefirmware muss diese Bereiche unterstützen.

| Aktion | Wirkung |
| --- | --- |
| Standard wiederherstellen | Vorschaufarben zurücksetzen |
| Vom Gerät lesen | Vorschau durch aktuelle Gerätefarben ersetzen |
| Auf Gerät anwenden | Farben ohne dauerhafte Speicherung anzeigen |
| Auf Gerät speichern | Farben anwenden und dauerhaft speichern |

Kurze Beschreibungen erscheinen beim Darüberfahren. Wenn ein Gerätebereich unverändert bleibt, die Firmware-Unterstützung prüfen.

<a id="settings"></a>
## Sprache, Darstellung und Geräteinformationen

Unter **Oberflächensprache** stehen 简体中文, English, Deutsch, 日本語 und Français zur Auswahl. Die Auswahl wird gespeichert und ändert nicht die Gerätesprache. Versionshinweise verwenden vom Herausgeber bereitgestellte Übersetzungen; Gerätedaten bleiben unverändert.

Über die Seitenleiste lassen sich helles/dunkles Design und Navigation umschalten. Desktop-Darstellung und Gerätefarben werden getrennt eingestellt. Die Einstellungen zeigen Modell, Firmware, vollständige Seriennummer und Produktionslos; über Aktualisieren können sie erneut gelesen werden. Bei Problemen hilft das Aktivitätsprotokoll.

<a id="software-update"></a>
## UCE Tool aktualisieren

Hiermit wird die **Desktop-Anwendung**, nicht die Gerätefirmware aktualisiert. Unter Windows **Über → Nach Updates suchen** im Fenstermenü wählen; unter macOS im Systemmenü **UCE → Nach Updates suchen**.

Bei einem passenden Update den Anweisungen folgen. Andernfalls das passende Paket auf der Release-Seite herunterladen und die alte Anwendung nach dem Beenden ersetzen. Vorher laufende Gerätefirmware-Vorgänge abschließen. Alte Mac-Versionen ohne DMG-Update-Unterstützung benötigen einmalig eine manuelle Installation der neuen Version.

<a id="faq"></a>
## Fehlerbehebung

- **Nicht verbunden:** Datenkabel und USB-Port prüfen, andere serielle Programme schließen und passende APP-Firmware sicherstellen. Falls das System das Gerät erkennt, aber UCE Tool nicht, das Protokoll prüfen.
- **Keine Messwerte:** Verbindung prüfen und Erfassung starten. Im pausierten Zustand oder BOOT-Modus gibt es keine Live-Messwerte.
- **E-Marker-Wert unbekannt:** Kabel oder Firmware meldet das Feld möglicherweise nicht. VDO-Rohdaten und weitere Ergebnisse prüfen.
- **GitHub-Anfrage fehlgeschlagen oder begrenzt:** Netzwerk und Proxy prüfen, später oder über ein anderes Netz erneut versuchen und die Fehlermeldung aufbewahren. Bei Zertifikatfehlern einer alten Mac-Version eine neuere Version mit Zertifikatkorrektur installieren.
- **Gerätefarben ändern sich nicht:** Gerät verbinden und Farben anwenden oder speichern; Firmware-Unterstützung prüfen. Für dauerhafte Änderungen speichern.
- **Welche Mac-Datei?** `arm64` für Apple Silicon, `x86_64` für Intel; siehe „Über diesen Mac“.
- **Automatisches Software-Update nicht verfügbar:** Passendes Paket von der Release-Seite laden und die beendete alte Anwendung manuell ersetzen.

Für eine Fehlerbeschreibung bitte Betriebssystem und Prozessor, UCE-Tool-Version, Gerätehardware und APP-Firmware, Schritte, vollständige Fehlermeldung oder Screenshot sowie relevante Protokolle angeben.
