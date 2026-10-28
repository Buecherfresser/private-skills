---
name: github-schreibstil
description: "Jonas' Schreibstil für alles, was sein Agent auf GitHub ans Team schreibt: Hinweis auf den Agenten, Kleinschreibung, lockerer Ton, Screenshots und Diagramme, wo sie helfen. Baut auf jonas-writing-style auf und wird von pr-schreiben, pr-kommentieren und issue-schreiben geladen. Direkt verwenden für andere GitHub-Texte in Jonas' Namen, etwa Antworten im Review oder Release-Notizen."
---

Lade vor dem Schreiben den Skill `jonas-writing-style` und befolge ihn. Er regelt die Grundlagen: Alltagssprache aus Sicht des Lesers, keine Namen aus dem Code, Abkürzungen ausschreiben, Länge, und für deutsche Texte `natural-german-2`. Dieser Skill ergänzt, was nur für GitHub-Texte in Jonas' Namen gilt, und hat Vorrang, wo sich beide widersprechen.

Was in einen Text gehört und wie er aufgebaut ist, legt der Skill für die jeweilige Textsorte fest (PR, Issue, Kommentar). Er hat wiederum Vorrang vor diesem.

## Hinweis auf den Agenten

Die erste Zeile ist immer "(geschrieben von jonas' agent)", bei englischen Texten "(written by jonas' agent)". Danach folgt eine Leerzeile. Die Zeile "Generated with Claude Code" kommt nicht ans Ende, der Hinweis oben ersetzt sie.

## Ton

- Locker und direkt, so wie Jonas mit seinem Team schreibt. Keine Slang-Wörter einbauen, nur um locker zu klingen.
- Offen sagen, wenn etwas erwartbar noch hakt oder fehlt ("ist logisch, dass das noch fehlt, weil ...").

## Schreibung

- Fließtext: Satzanfang groß, alles andere klein, auch Substantive ("Bisher musste der support jedes vergessene passwort von hand zurücksetzen").
- Stichpunkte, Zwischenüberschriften und kurze Kommentare komplett klein.
- Abkürzungen, die man groß schreibt, bleiben groß (API, PDF, SSO). Titel verlinkter Issues und PRs bleiben, wie sie sind.

## Verweise und Details

- Keine nackten Verweise wie "#36" oder Migrationsnummern wie "V54". Issues und PRs immer mit ihrem Titel als Link nennen ("der PR zum passwort-reset").
- Keine Testzahlen ("2366 Tests"), keine Listen aller berührten Module und keine Reihenfolgen über einzelne Dateien. Gibt es ausführliche Doku, verlinke sie in einem Satz.
- Allgemeine Entwicklerbegriffe wie Branch, Merge, Migration, Datenbank, Tests und API sind in Ordnung.

## Visuelle Elemente

Wo ein Bild etwas schneller zeigt als Text, nutze es. Ein guter Screenshot ersetzt oft einen ganzen Absatz, deshalb lohnt es sich, bei jedem Text kurz zu überlegen, ob eins passt.

- **Screenshots** für alles, was man sieht: eine neue Seite, ein geändertes PDF, eine Fehlermeldung. Ändert sich etwas Sichtbares, gern vorher und nachher nebeneinander. Hochgeladen werden Bilder über den Bilder-Branch (siehe unten).
- **Tabellen** für Vergleiche, etwa vorher und nachher oder mehrere Fälle mit ihrem Ergebnis.
- **Diagramme** für Abläufe mit mehreren Schritten oder Beteiligten, als Mermaid-Codeblock (```` ```mermaid ````), den GitHub direkt darstellt. Höchstens etwa sieben Kästen, beschriftet in Alltagssprache.

Kein Bild als Deko und keins, das nur wiederholt, was schon im Text steht. Kurze Kommentare kommen meist ohne aus.

### Bilder hochladen

`gh` kann keine Bilder an PRs, Issues oder Kommentare hängen. Bilder kommen deshalb in einen eigenen, leeren Branch `bilder` im selben Repo, der nie gemergt wird. So bleiben sie aus dem Code heraus.

Gibt es den Branch noch nicht, leg ihn einmal leer an. Diese Befehle ändern nichts am aktuellen Arbeitsstand:

```bash
SHA=$(git commit-tree "$(git hash-object -w -t tree /dev/null)" -m "chore: leerer branch für bilder")
git push origin "$SHA":refs/heads/bilder
```

Jedes Bild lädst du dann über die API hoch, ohne den Branch auszuchecken. Leg es in einen Ordner, der nach dem PR oder Issue benannt ist, damit man es später zuordnen kann:

```bash
gh api -X PUT repos/<owner>/<repo>/contents/<ordner>/<name>.png -f message="docs: bild für <thema>" -f branch=bilder -f content="$(base64 -i <datei>.png)"
```

Im Text bindest du es mit diesem Link ein. Er funktioniert auch in privaten Repos für alle, die Zugriff haben:

```markdown
![kurze beschreibung](https://github.com/<owner>/<repo>/blob/bilder/<ordner>/<name>.png?raw=true)
```

## Fragen zu Dokumenten

Beruht eine Frage oder Unsicherheit auf einer Stelle in einem Dokument, zeig dem Leser genau diese Stelle, damit er nicht selbst suchen muss. Nenne immer das Dokument und die Seite oder den Abschnitt dazu.

Ob Screenshot oder Zitat, hängt davon ab, was dem Leser mehr hilft:

- **Screenshot**, wenn das Aussehen der Stelle zählt oder sich der Text nicht sauber abschreiben lässt: Layout, Tabellen, Grafiken, Formeln, Formatierung. Das gilt fast immer für PDFs und oft für HTML-Seiten, Folien oder Word-Dokumente. Markiere den Abschnitt, um den es geht, etwa mit einem farbigen Rahmen, und schneide das Bild so zu, dass die Stelle mit etwas Umfeld lesbar bleibt. Eine PDF-Seite lässt sich zum Beispiel mit `pdftoppm -png -r 150 -f <seite> -l <seite>` rendern, eine HTML-Seite im Browser aufnehmen. Markieren und zuschneiden geht mit ImageMagick oder Python (Pillow). Eingefügt wird der Screenshot wie oben beschrieben.
- **Zitat**, wenn der Text allein reicht, etwa bei Markdown, reinem Text, CSV oder Code: die Stelle als Blockzitat (`>`) übernehmen. Verlinke die Datei, auf GitHub am besten mit Zeilenangabe (`datei.md#L10-L14`).

## Vor dem Posten

Zeig dem Nutzer den fertigen Text, bevor du ihn auf GitHub anlegst oder änderst, außer er hat schon gesagt, dass du ihn direkt posten sollst. Übergib längere Texte mit `--body-file`, damit Umbrüche und Sonderzeichen erhalten bleiben.
