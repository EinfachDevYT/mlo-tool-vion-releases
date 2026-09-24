# Tutorial: Vom leeren Projekt zum fertigen FiveM-MLO

Ohne Blender, ohne Sollumz. Du brauchst nur das **Vion MLO Tool**, **CodeWalker** und einen **FiveM-Server**.
Am Ende steht ein zweistöckiges Haus mit Haustür, Fenstern, Treppe und Möbeln auf deinem Server.

Dauer: etwa 20–30 Minuten beim ersten Mal.

---

## 0. Was ist ein MLO – und was baut das Tool?

Ein **MLO** ist ein begehbarer Innenraum in GTA V. Er besteht aus **Räumen** und **Portalen**:
GTA zeichnet einen Raum nur, wenn du dich in ihm befindest oder durch ein Portal (Tür, Fenster,
Durchgang, Treppenloch) hineinschaust. Deshalb gilt: **Jeder Raum braucht eine Verbindung.**

Das Tool erzeugt beim Export automatisch:

| Datei | Inhalt |
|---|---|
| `name.ytyp` | das MLO mit Räumen, Portalen und Objekten (Türen, Möbel) |
| `name_r1.ydr`, `name_r2.ydr` … | ein 3D-Modell pro Raum, Texturen eingebettet |
| `name_shell.ydr` | die **Außenhülle** – damit das Gebäude auch von außen sichtbar ist |
| `name_col.ybn` | die Kollision (Wände, Böden, Treppen als Rampe) |
| `name.ymap` | die Platzierung in der Welt |
| `fxmanifest.lua` | die fertige FiveM-Ressource |

Damit baust du **komplette kleine Gebäude**, nicht nur Innenräume.

---

## 1. Einrichten (einmalig)

1. **Vion MLO Tool** installieren: `Vion-MLO-Tool-Setup-x.y.z.exe` aus den
   [Releases](https://github.com/EinfachDevYT/mlo-tool-vion-releases/releases) starten.
2. **CodeWalker** herunterladen und entpacken (falls noch nicht vorhanden).
3. Im Tool: **Zahnrad (Einstellungen) → CodeWalker → „Ordner wählen…“** und den Ordner auswählen,
   in dem `CodeWalker.exe` liegt.

   ✓ Danach erzeugt der Export die GTA-Dateien direkt – du musst in CodeWalker nichts mehr importieren.

---

## 2. Einen Bauplatz finden

Das MLO wird an einer festen Stelle der Karte platziert. Such dir eine **freie, ebene Fläche**
(das MLO entfernt keine vorhandenen Gebäude oder Bäume).

- Im Spiel mit einem Koordinaten-Befehl deines Servers (z. B. aus vMenu) oder
- in CodeWalker (Weltansicht, unten stehen die Koordinaten der Kamera).

Notiere dir **X, Y, Z** – Z ist die Bodenhöhe. Den Wert trägst du in Schritt 11 ein.

> Am besten eignen sich **Asphalt- oder Betonflächen**. Auf Wiese wächst das Gras der Karte sonst durch
> deinen Fußboden. Trage Z dann **0,1–0,2 m höher** als die Bodenhöhe ein.

---

## 3. Das Erdgeschoss aufziehen

1. **Neues Projekt** auf der Startseite.
2. Taste **2** – Draufsicht. Das Raster steht oben auf **0,5 m**.
3. Werkzeug **Raum (R)**, mit gedrückter linker Maustaste ein Rechteck aufziehen,
   z. B. **8 × 6 m**. Unten links siehst du die Maße live.

   Es entstehen: Boden, Decke und vier Wände. Die Innenseite der Wände heißt **Seite A**,
   die Außenseite **Seite B**.

> Tipp: Rechte Maustaste dreht die Kamera (in der 3D-Ansicht, Taste **1**),
> Mausrad zoomt, **F** holt alles ins Bild.

### Weitere Räume

Zieh einfach direkt daneben ein zweites Rechteck auf. Die gemeinsame Wand wird **nur einmal** erzeugt.
Jeder Boden ist ein Raum; im Eigenschaften-Panel rechts kannst du ihn umbenennen
(z. B. „Wohnzimmer“, „Bad“). Böden mit dem gleichen Namen gehören zum selben Raum.

### Innenwände

Werkzeug **Wand (W)**: Punkte nacheinander anklicken, **Doppelklick** oder **Enter** beendet.
Mit gedrückter **Umschalt**-Taste rasten Wände auf 45°-Schritte ein, Wandenden rasten an bestehende an.

---

## 4. Türen, Fenster, Durchgänge

| Werkzeug | Taste | Wofür |
|---|---|---|
| **Tür** | T | setzt eine echte GTA-Tür (Prop) + Öffnung |
| **Fenster** | N | Öffnung mit Glasscheibe und Brüstung |
| **Durchgang** | G | offene Öffnung ohne Tür, z. B. Wohnzimmer → Küche |

Werkzeug wählen, mit der Maus über eine Wand fahren (farbige Vorschau = passt, rot = passt dort nicht) und klicken.
Rechts lassen sich Position, Breite, Höhe und Brüstung einstellen. Unter „Tür-Objekt“ wählst du das
Türmodell, bei Bedarf gibst du einen eigenen Prop-Namen ein.

**Wichtig:**

- Mindestens **eine Tür muss nach außen** führen, sonst kommt man nicht hinein.
- **Jeder Raum** braucht eine Tür, einen Durchgang oder eine Treppe zu einem anderen Raum.
  Aus diesen Öffnungen werden automatisch die Portale.

---

## 5. Texturen

Unten ist der Texturen-Browser. Zwei Wege:

- **Ziehen:** Textur mit der Maus direkt auf eine Fläche in der 3D-Ansicht ziehen.
  Innenseite, Außenseite, Boden, Decke – jede Fläche einzeln.
- **Klicken:** Element auswählen, rechts das Texturfeld anklicken (z. B. „Seite B“), dann unten eine Textur.

Weitere Knöpfe bei Wänden: **„Auf alle Wände“** und **„Seiten tauschen“**.

Eigene Texturen: **Importieren** oder PNG/JPG-Dateien direkt in den Browser ziehen.
Über „⋯“ an der eigenen Textur stellst du Kachelgröße, Kollisionsmaterial (Holz, Fliesen …) und
„Transparent“ (für Glas) ein.

---

## 6. Ein Obergeschoss bauen

1. Nichts ausgewählt → rechts **Projekt → „Etage darüber hinzufügen“**.
   Böden, Wände und Fenster werden eine Etage höher kopiert, die Ebene springt auf **3 m**.
2. Im Obergeschoss kannst du jetzt wie gewohnt weiterbauen (Wände, Fenster, Texturen).
3. Mit **Bild↓** zurück ins Erdgeschoss.

> Solange **Decken** ausgeblendet sind (Taste **H**), sind auch höhere Etagen ausgeblendet –
> so siehst du immer die Ebene, an der du arbeitest.

---

## 7. Die Treppe

1. Im **Erdgeschoss** (Ebene 0 m) das Werkzeug **Treppe (S)** wählen.
2. Vom **Treppenfuß** zum **oberen Ende** ziehen. Die Statusleiste zeigt Länge, Stufen und Steigung –
   angenehm sind **30–38°** (bei 3 m Höhe ca. **4–5 m** Länge).
3. Fertig: Die Treppe schneidet **automatisch** ein Loch in den Boden darüber, bekommt eine
   Rampen-Kollision (Figuren laufen sauber hoch) und ein Portal zwischen den Etagen.

Rechts kannst du Breite, Höhe und Richtung ändern.

### Geländer

- **An der Treppe:** Treppe auswählen → rechts unter **Geländer** „Beide Seiten“, „Nur links“,
  „Nur rechts“ oder „Kein Geländer“. Läuft die Treppe an einer Wand entlang, reicht eine Seite.
  Der Handlauf steigt mit der Treppe mit.
- **Rund um das Treppenloch oben:** Ebene auf **3 m** (Bild↑), Werkzeug **Geländer (L)**, vom Anfang zum
  Ende ziehen. Mit gedrückter **Umschalt**-Taste rastet es auf 45°-Schritte ein. Pro Seite des Lochs
  ein Geländer ziehen – die Seite, an der man oben ankommt, frei lassen.

Geländer haben eine unsichtbare Kollision bis zum Handlauf, man kann also nicht hindurchfallen.

---

## 8. Decken und Dach

- Jeder Raum aus dem Raum-Werkzeug hat bereits eine Decke. Im Boden-Panel: **Decke erzeugen**,
  **Deckenhöhe** sowie die Texturen **Decke (innen)** und **Dach (außen)**.
- Das Werkzeug **Decke (D)** zieht eine freie Deckenplatte auf – z. B. über einem Balkon oder Vordach.
- Die **Unterseite** eines Bodens ist die Decke des Raums darunter (Texturfeld „Unterseite“).

---

## 9. Möbel und Objekte

Werkzeug **Prop (P)** → klicken. Rechts den **Modellnamen** eintragen (z. B. `prop_couch_01`,
`prop_table_03`) – jedes GTA-V-Modell funktioniert. **Q/E** dreht, Ziehen verschiebt.

---

## 10. Licht und Stimmung

Jeder Raum hat einen **Timecycle** (Projekt-Panel → Räume). Er bestimmt Helligkeit und Farbstimmung
im Innenraum. `int_gasstation` ist ein heller, neutraler Standard – probier die anderen Einträge aus
und vergleiche im Spiel.

---

## 11. Weltposition

Nichts ausgewählt → rechts **Position in der GTA-Welt**: die Koordinaten aus Schritt 2 eintragen.
**Drehung** dreht das ganze Gebäude um die Hochachse.

---

## 12. Exportieren

1. **Strg+E** (oder oben rechts „Export“).
2. Ressourcen-Name prüfen (nur `a-z`, `0-9`, `_`), Zielordner wählen, **Exportieren**.
3. Ist CodeWalker eingerichtet, erscheint **„Fertig – MLO ist startklar“**: Im Ordner
   `name/stream` liegen alle GTA-Dateien.

Der Export warnt dich vorher, z. B. wenn ein Raum keine Verbindung hat.

<details>
<summary>Ohne eingerichteten CodeWalker-Ordner (Umwandlung von Hand)</summary>

1. CodeWalker → **Tools → RPF Explorer**, oben **Edit mode** aktivieren.
2. Im GTA-Ordner einen leeren Ordner anlegen und öffnen (z. B. `mods\mein_mlo`).
3. Alle Dateien und Unterordner aus `name/codewalker_xml` hineinziehen (bzw. Rechtsklick → *Import XML*).
4. Die entstandenen `.ydr`, `.ybn`, `.ytyp`, `.ymap` nach `name/stream` kopieren.

</details>

---

## 13. Auf den Server bringen

1. Den Ordner `name` in den `resources`-Ordner deines Servers kopieren.
2. In der `server.cfg`: `ensure name`
3. Server neu starten, zur Weltposition gehen – fertig.

---

## Fehlerbehebung

| Problem | Ursache / Lösung |
|---|---|
| Raum ist von innen unsichtbar | Der Raum hat keine Tür/Durchgang/Treppe zu einem anderen Raum → Öffnung setzen. |
| Gebäude ist von außen unsichtbar | Die `name_shell.ydr` fehlt in `stream` oder die `.ymap` ist nicht dabei. |
| Man fällt durch den Boden | Die `name_col.ybn` fehlt in `stream`, oder die Z-Koordinate liegt unter dem Gelände. |
| Alles weiß ohne Texturen | Alte Export-Version – mit der aktuellen Version neu exportieren (Texturen sind jetzt eingebettet). |
| Gebäude steckt im Boden / schwebt | Z-Koordinate der Weltposition anpassen. |
| Gras wächst durch den Fußboden | Z der Weltposition 0,1–0,2 m höher setzen oder auf Asphalt/Beton bauen. |
| Graue Leere um die Figur, Tür steht neben dem Haus | Teile wurden einzeln verschoben (alte Version: Außenhülle separat). Position **nur im Tool** ändern und neu exportieren – seit 1.1.2 ist die Außenhülle Teil des MLO und bewegt sich immer mit. |
| Änderungen kommen nicht an | FiveM-Cache leeren (`%localappdata%\FiveM\FiveM.app\data\cache`) und Server neu starten. |
| Tür passt nicht in die Öffnung | Breite der Öffnung an die Tür anpassen oder anderes Tür-Modell wählen. |

## Grenzen der aktuellen Version

- Böden und Decken sind Rechtecke (Formen entstehen durch mehrere Rechtecke).
- Treppen sind gerade (keine Wendel- oder L-Treppen – dafür zwei Treppen mit Podest bauen).
- Keine eigenen Lampen-Objekte im Modell; die Helligkeit kommt vom Timecycle. Lampen-Props kannst du als Prop platzieren.
- Keine LOD-Modelle: Aus großer Entfernung (ca. 300 m) wird die Außenhülle ausgeblendet.
