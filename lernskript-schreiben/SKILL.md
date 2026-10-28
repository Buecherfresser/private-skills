---
name: lernskript-schreiben
description: "Erstellt ein Lernskript zu einem beliebigen Thema als LaTeX-Dokument und kompiliert es zu PDF. Verwenden, wenn jemand ein Lernskript, Skript, Studienskript oder eine Einführung als LaTeX/PDF möchte."
---

# Lernskripte mit LaTeX erstellen

Ziel ist ein Skript, mit dem die Zielgruppe ein Thema wirklich versteht und anwenden kann, nicht nur eine Sammlung von Fakten. Der Ablauf unten gilt für jedes Thema. Er ist bewusst grob und wird an Thema, Umfang und Zielgruppe angepasst.

## 1. Auftrag klären

Vor dem Schreiben klären (kurz nachfragen, wenn es nicht aus der Anfrage hervorgeht):

- **Zielgruppe und Vorwissen:** Einsteiger, Fortgeschrittene, Praktiker (z. B. Entwickler statt Sachbearbeiter)? Davon hängen Tiefe und Beispiele ab.
- **Umfang:** ungefähre Seitenzahl. Sie bestimmt, wie viele Kapitel und Abbildungen sinnvoll sind.
- **Schwerpunkte:** Welche Teile sollen ins Detail gehen, welche reichen als Überblick?
- **Quellen:** Hat die Person eigene Unterlagen, Daten oder Grafiken? Diese bevorzugt verwenden.
- **Sprache:** In welcher Sprache soll das Skript sein? Ohne Angabe gilt die Sprache der Anfrage.

## 2. Recherche zuerst, dann schreiben

- Erst alle Fakten sammeln, dann die Gliederung bauen. Nicht während des Schreibens recherchieren.
- Für Themen, die sich ändern (Normen, Versionen, Gesetze, Software), den aktuellen Stand im Web prüfen und den Stand im Skript nennen ("Stand: Monat Jahr, Version X").
- Primärquellen bevorzugen (Originaldokumente, Normen, offizielle Doku). Sekundärquellen nur ergänzend und kritisch.
- Umfangreiche Recherchen an parallele Subagenten geben, die ihre Ergebnisse als Notizdatei mit Quellenangaben ablegen. Unsicheres dort ausdrücklich als UNSICHER markieren lassen.
- Nichts erfinden: Was sich nicht belegen lässt, wird weggelassen oder als Einschätzung formuliert.

## 3. Gliederung

Bewährter Aufbau, je nach Thema anpassen:

1. Titelseite mit Stand, Zielgruppe und einem kurzen Kasten "Wie du dieses Skript liest"
2. Inhaltsverzeichnis
3. Grundlagen und Begriffe: das Fundament, auf dem alles Weitere aufbaut
4. Zusammenhänge und Regelwerk bzw. Theorie
5. Detailkapitel zum Schwerpunkt, mit durchgerechneten Beispielen
6. Praxis bzw. Umsetzung: typische Fehler, Checkliste, Übungen oder Testfälle
7. Anhang: Abkürzungen, Glossar, Quellen

Jedes Kapitel baut auf dem vorherigen auf. Die Kapitelüberschriften sagen konkret, worum es geht. Generische Titel wie "Fazit" vermeiden.

## 4. Sprache und Stil

Lade vor dem Schreiben den Skill `natural-german-2` und befolge ihn. Er regelt Satzbau, Zeichensetzung, Anrede und Formulierungen. Bei Skripten in anderen Sprachen seine Regeln sinngemäß übertragen, im Englischen etwa "you" statt "one" und kurze aktive Sätze.

Speziell für Lernskripte gilt zusätzlich:

- Jeden Fachbegriff beim ersten Auftreten erklären, Abkürzungen beim ersten Mal ausschreiben und im Anhang sammeln.
- Das Niveau an der Zielgruppe ausrichten: Einsteiger brauchen Herleitungen, Praktiker brauchen Details und Sonderfälle.
- Quellen gehören in Bildunterschriften, Tabellen und den Anhang, nicht in den Fließtext.
- In LaTeX die passende Sprache setzen (`\setdefaultlanguage{english}` usw.), damit Silbentrennung und Bezeichnungen wie "Inhaltsverzeichnis" stimmen.

## 5. Inhaltliche Qualität

- **Konkret statt abstrakt:** Zahlen, Rechenwege, echte Beispiele, ein durchgehendes Fallbeispiel.
- **Didaktische Elemente:** Merke-Kästen für Kernaussagen, Praxis- bzw. Expertenkästen für Vertiefung, Tabellen für Vergleiche, Formeln für Rechenwege.
- **Grafiken, wo sie etwas erklären:** Abläufe, Strukturen, Zeitstrahlen, Hierarchien. Eigene Diagramme mit TikZ zeichnen. Bildschirmfotos oder Auszüge aus Originaldokumenten einbinden, wenn verfügbar (PDF-Seiten mit `pdftoppm` rendern und zuschneiden), immer mit Quellenangabe in der Bildunterschrift.
- **Kein Ballast:** keine Wiederholungen derselben Aussage in Einleitung, Hauptteil und Schluss, keine Füllsätze.
- **Ehrlich zu Grenzen:** Wenn Quellen nicht vollständig lesbar waren oder Abbildungen nachgebaut statt kopiert sind, das kurz im Skript vermerken.

## 6. Technische Umsetzung

- Projekt in mehrere Dateien aufteilen: `main.tex` (Präambel) plus eine Datei je Kapitel, eingebunden mit `\input`. So bleiben Korrekturen übersichtlich.
- **Compiler:** `xelatex` mit `fontspec` (zweimal kompilieren für Inhaltsverzeichnis und Verweise). Falls `lualatex` scheitert (z. B. fehlendes `luaotfload`), auf `xelatex` ausweichen.
- **Sprache in LaTeX:** Für Deutsch `polyglossia` mit `\setdefaultlanguage[spelling=new]{german}`. Prüfen, ob Silbentrennmuster installiert sind (`kpsewhich hyph-de-1996.tex`), sonst `texlive-lang-german` nachinstallieren. Deutsche Anführungszeichen `\glqq`/`\grqq` bei Bedarf selbst definieren.
- **Schriften:** Nur OpenType-Schriften verwenden, die `fc-list` bzw. `kpsewhich` findet (z. B. TeX Gyre Pagella für Text, eine Sans-Schrift für Überschriften, DejaVu Sans Mono für Code). Type1-Schriften führen unter xelatex oft zu Treiberfehlern.
- **Bewährte Pakete:** `geometry`, `microtype`, `booktabs`/`tabularx`, `tcolorbox` (Kästen), `tikz`, `listings` (Code), `caption`, `fancyhdr`, `titlesec`, `float`, `needspace` (verhindert Überschriften am Seitenende), `rotating` (breite Grafiken im Querformat), `hyperref`.
- Eine Akzentfarbe und eine kleine Farbpalette in der Präambel definieren und überall verwenden.
- `\setlength{\emergencystretch}{2em}` gegen überlange Zeilen. In Fließtext kein `--` verwenden, wenn der Schreibstil keine Gedankenstriche erlaubt, denn LaTeX macht daraus einen Halbgeviertstrich.

## 7. Prüfen vor der Abgabe

1. **Kompilieren:** keine Fehler, Overfull-Warnungen prüfen (`grep Overfull build.log`).
2. **Visuell prüfen:** Seiten mit `pdftoppm -r 70` rendern, zu Kontaktbögen zusammensetzen und ansehen. Achten auf: überlappende Beschriftungen in TikZ-Grafiken, zu kleine Grafiken, verwaiste Überschriften, Inhaltsverzeichnis mit einzelner Restseite, Text über dem Rand.
3. **Fakten prüfen:** Bei umfangreichen oder kritischen Inhalten einen Subagenten das Skript gegen die Recherchenotizen prüfen lassen (Widersprüche, unbelegte Aussagen, Rechenfehler, Beispiele auf innere Stimmigkeit).
4. **Sprache prüfen:** Text mit `pdftotext` extrahieren und nach Zeichen und Floskeln suchen, die der Stil-Skill verbietet, etwa mit `grep -n -E "–|—|;"`. Treffer im Quelltext beheben.
5. Umfang mit `pdfinfo` kontrollieren und mit dem Auftrag abgleichen.

## 8. Auslieferung

- PDF und ein ZIP mit allen LaTeX-Quellen und Abbildungen ausliefern, damit die Person selbst weiterarbeiten kann.
- In der Antwort kurz sagen, was drin ist, auf welchem Stand das Skript ist und wo Grenzen liegen (z. B. nicht prüfbare Stellen). Keine lange Nacherzählung des Inhalts.
- Fallen später Fehler auf, das Skript korrigieren, neu kompilieren und die Änderung benennen.