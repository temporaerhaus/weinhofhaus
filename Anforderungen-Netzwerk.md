
# Weinhofhaus: Konzept Netzwerk

Status: grobe Skizze.

Anlagen:
* *[weinhofhaus-schema-netzwerk.pdf](weinhofhaus-schema-netzwerk.pdf)* – Skizze für eine Soll-Netzwerkinfrastruktur im Haus.
* *[raumbezeichnungen.csv](raumbezeichnungen.csv)* – Tabelle Raumnummern und Bezeichnungen.
* *[netzwerkanschluesse-bestand.csv](netzwerkanschluesse-bestand.csv)* – Tabelle Bestand Netzwerkanschlüsse Verschwörhaus; gezählt wurden mögliche Gigabit-Anschlüsse (alle 4 Aderpaare + Schirm = 1 Anschluss).
* *[netzwerkanschluesse-soll.csv](netzwerkanschluesse-soll.csv)* – Tabelle benötigte Netzwerkanschlüsse; angegeben sind Cat6<sub>A</sub>-Anschlüsse (Gigabit).



## Überblick

### Hausanschlüsse (Internetzugänge)

* SWU Telenet kommt mit Glasfaser in #9 U1 an.
* Telekom kommt mit 100 DA in #7/10 U1 an.
* Gibt es weitere Anbieter und Positionen für Hausanschlüsse?

→ Zentraler Raum ist in #7/10 U1 "Serverraum" **=: RZ1**.



### Netzwerk

Von RZ1 aus auf jedes Stockwerk/jeden Stockwerksteil in jedem Haus:
* 12 Fasern LWL (9/125 µm, OS2).
* Ggf. als Reserve weitere 6 Fasern LWL parallel dazu verlegen (s.u.).
* Idealerweise MPO/MTP Trunkkabel um selbst auf Panel auflegen zu können.

Vom Verteiler (DV, auch Netzwerkschrank) in jedem Stockwerk/Stockwerksteil:
* Genügend Gigabit per Kupfer in die Räume verteilen (Cat6<sub>A</sub> bzw. Class E<sub>A</sub>).
* S.u. für Tabelle zur Mengenschätzung nach möglichen Büroarbeitsplätzen.

LWL-Backbone zwischen den Häusern, je 48+ Fasern (9/125 µm, OS2):
* von RZ1 nach "Hausanschlussraum" in #9.
* von RZ1 nach "Server" in #6.

Cat-Verbindungen (Kupfer) in die DV aller Stockwerke/Stockwerksteile (oder nach RZ1):
* 2×2 Cat6<sub>A</sub> vom jeweiligen U1 aus (RZ0, RZ1, RZ2).
* (!) Wo enden diese Leitungen? Besser wäre sie würden auch alle in RZ1 enden, aber wollen wir wirklich Kupfer zwischen Gebäuden? (Auch wenn die Wand an Wand stehen.)



#### Rechenzentrum

Da Haus für's Digitale, wird auch ein Rechenzentrum (RZ) benötigt. Jedoch nur als Experimentierfeld und nicht als vollwertiges RZ für produktive Dienste, d.h. mit Redundanz, vollem Datenschutz/-sicherheit (z.B. Erfüllung des BSI-Grundschutzkatalogs etc.).

* 4× Serverschränke in RZ1.
* Klimatisierung.
  * Alte zweite Klima zurückbauen oder besser für Redundanz wieder ertüchtigen?
* Zugangskontrolle/-konzept?
  * Grundsätzlich sind die Schränke in RZ1 abgeschlossen, da viele Personen haben Zugang zum Raum insgesamt.



## Grundsätze und Annahmen

* Nutzung durch **viele verschiedene Organisationen** möglich:
  * 14 oder mehr Organisationen <== augenscheinlich ersichtliche Aufteilung der drei Häuser und der (teilw. geteilten/teilbaren) Stockwerke.
  * mit jeweils unterschiedliche Anforderungen ans Netzwerk/Internetzugang (Art der Nutzung; Datenschutz und -sicherheit; ...)
    * → physikalisch getrennte Netze sind möglich (Bsp. separates Netz für Teile der Stadtverwaltung oder Caritas etc.).
    * → Nutzung jeweils eigener ISPs ist möglich.
* Der Komplex „Weinhofhaus“ (Weinhof 6, 7/10 und 9) wird von Organisationen genutzt, die einen **„überdurchschnittlichen digitalen Bedarf“** haben. D.h. z.B., dass etwas „mehr Netzwerk“ vorgesehen werden muss als für aktuell moderne Büroarbeitspläze.
* Der Ausbau in den jeweiligen Stockwerken der einzelnen Häuser könnte anlassbezogen erfolgen (zwischen Auszug und neuem Einzug und z.B. zusammen mit Erneuerung Böden und Deckenabhängungen).
* Glasfaser (LWL):
  * single mode, 9/125 µm, OS2.
  * LC ports female am Patchfeld, PC.
    * E2000 wäre besser, ist aber kostenintensiver. --sl
      * Ich wuerde dann auch E2000 vorsehen. Stadt/SWU macht das so. --stk
      * E2000 ist Overkill auf diesen Strecken. Lieber modulare LC/LC Koppler. Von Einfügedämpfung her recht ähnlich (FS.com < 0.2dB) aber billiger und flexibler --jaydi
* Kupfer (Cat)
  * Cat 6<sub>A</sub>/Class E<sub>A</sub>, RJ45; also ≥ 1 Gigabit “to the desk”.
* Modularität:
  * Grundsätzlich sind Trunkkabel bevorzugt gegenüber zu spleißenden Kabeln. 
  * Trunkkabel zwischen einzelnen Schränken, um Glasfaser-Patchfelder nachziehen zu können.


## Stockwerksverteilung

Strukturierte Verkabelung auf die Stockwerke/Stockwerksteile der drei Häuser. Auf jedem Stockwerk/in jedem Stockwerksteil der einzelnen Häuser (9, 7/10, 6) befindet sich ein „halbhoher“ Netzwerkschrank (~9 HE).

Details zum Netzwerkschrank (DV):
* Wandmontage, so dass darunter mit min. 15 cm Abstand noch ein zweiter „halbhoher“ DV für eine weitere Organisation montiert werden könnte.
* Cat-Verbindungen mit in Panel eingeklickten RJ45-Modulen. Genügend überstehende Leitungslänge vorsehen, so dass die Leitungen auch in den optionalen unteren DV verlegt und die Module dort eingeklickt werden können.
* Schließung der DV: da die Räume mit den DV allgemein zugänglich sein werden, eine Schließung mit Halbzylindern oder eine digitale Schließung der Schränke vorsehen.
* Dimensionen DV, ca. B×T×H: 70+ × 55+ × 100 cm; 18 HE
* Uplink:
  * LWL aus RZ1: 6 Fasern = 3 Duplexanschlüsse pro DV (MPO?).
  * Cat aus RZ1 oder dem jew. UG: 2×2 Kupferleitungen.



### Anzahl Anschlüsse

#### ... als Büro genutzte Räume

Grundlage:
* 2× je Arbeitsplatz: PC, Telefon.
* 4× pauschal pro Raum/Büro: z.B. 1× Drucker, 1× AccessPoint, 1× Beamer o.ä., 1× Klingel-/Gegensprechanlage o.ä..
  * Nur wenn eines dieser Geräte nicht benutzt wird gibt es mit der in der Tabelle angegebenen Mindestanzahl noch eine Reserve.

| max. Anz. Arbeitsplätze | min. Anz. Anschlüsse | großzügigere Anz. Anschlüsse |
|----:|----:|----:|
|  1 |  6 |  8 | 
|  2 |  8 | 10 |
|  3 | 10 | 12 |
| +1 | +2 | +2 |

*Tabelle: Anzahl Anschlüsse*

NutzerInnen:
* Gigabit an jedem Anschluss (Class E<sub>A</sub>).
* In den Räumen sind die Anschlüsse in Brüstungskanälen oder Bodentanks.
* Je 2 der Anschlüsse sind in/an der Decken zu verbauen (WLAN, Beamer, Infomonitore, Gegensprechanlage, IoT-Funk, Lautsprecher etc.).
  * Strom sollte auch in der Decke vorgesehen werden: 2× Schuko.



#### ... sonstige Flächen

* Flure, Empfang, WCs, Treppenhäuser, ...?
* min. vom Boden erreichbare 2× Anschlüsse + 2× in der Decke.
* Konzept und Auflistung der Anschlüsse kann gerne erstellt werden.
* Erschließung der Türen (Außenhaut, sowie von Treppenhäusern o.ä. abgehend)? Z.B. für (zeit-)gesteuerte Summerfunktion zur öffnung von nicht-verschlossenen Türen.
* Glasfaser als Reserve in die Dachstühle von #7/10 und #6?


#### ... Außenwände

Vorschlag:
* 2× #7/10 zum Schwörhaus rüber (z.B. wegen Fahrradständern)
* 2× Weinhof
* 2× Gartenhof
* 2× zwischen #7/10 und #6 zur Synagoge rüber
* 2× Innenhof #6
* 2×2 Weinhofberg



## Rechenzentrum

RZ1 = zentraler Raum zur Netzwerkverteilung (alle drei Häuser) und als kleines Rechenzentrum.

* RZ0: "Serverraum" in #6
  * könnte bei Bedarf erschlossen werden.
* RZ1: im bisherigen "Serverraum" in #7/10 → "voll" ausgebaut.
  * Kabelpritschen oberhalb der Serverschränke, als „Rechteck“.
  * Klimatisierung
  * ...
* RZ2: "Hausanschlussraum" in #9
  * SWU/Telenet Glasfaser kommt hier an.
  * könnte bei Bedarf erschlossen werden, Klima war hier z.B. mal vorhanden.
  * ...



### Backbone

* 48+ Fasern LWL von RZ2 nach RZ1 und von RZ1 nach RZ0.



### Datenverteiler

* 1× „ganzer“ DV (ISPs ankommend und "Schaltstelle").
  * ankommend: ISPs, z.B. via DA (Telekom) oder 48 Fasern LWL aus #9 U1 (SWU/Telenet).
    *  100 DA Querverbindung zum Hausanschluss der Telekom?
  * abgehend: 16× 12 Fasern in die DVs der einzelnen Organisationen in RZ1.
* 16× viertelshoher DV (50 cm Höhe).
  * ankommend: 1× 12 Fasern aus DV "Schaltstelle"
  * abgehend, ins jeweilige Stockwerk/Stockwerksteil:
    * 1× 6 Fasern
    * evtl. 2× 2 Cat
* 4× ganzer DV: für Server etc.
  * je 1× am Stück an eine Organisation.



## Mengengerüst

Erste grobe Schätzung gerne nach Rücksprache, v.a. Rückkopplung wo's hingehen soll.


| Haus | Ebene | Summe Anschlüsse |
| ---:|  ---:| ---:|
|    9|    0 |  26 |
| 7/10|   U1 |  58 |
| 7/10|    0 |  90 |
| ... |  ... | ... |

*Tabelle: Anschlüsse Cat aufsummiert*



### Beispiele und Kalkulationen

Gerne nach Rücksprache mehr.

#### Backbone mit MPO?

https://www.cbo-it.de/de/wissen/124-was-ist-mpo-mtp-multiple-fiber-push-on-pull-off-im-ueberblick.html


#### Dimensionierung der Schränke?

Bsp. aus dem Verschwörhaus:

| Bezeichnung | H [cm] | B [cm] | T [cm] | HE |
| --- | ---: | ---: | ---: | ---: |
| kleiner bei Sabine | 50 | 60 | 53 | 9 |
| großer im Salon | 210 | 80 | 85 | 43 |
| Serverschrank in RZ1 | 200 | 80 | 100 | 42 |

_(1 HE =  = 4,445 cm)_


Tiefen von Geräten (Einbaukante am Raster bis Ende Anschlüsse):

| Bezeichnung | T [cm] |
| --- | ---: |
| HP 2626 PWR (J8164A) | 53 |
| Server/Storage | 83 |
| KVM-Konsole | 57 |
| ASR 9000 | 58 |
| Catalyst 6500 E | 46 |
