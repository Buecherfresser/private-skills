---
name: issue-schreiben
description: "Schreibt Titel und Text eines GitHub Issues in Jonas' Stil: deutsch, kurzer Kontext, was gerade fehlt oder hakt und was zu tun ist. Immer verwenden, wenn ein Issue angelegt oder sein Text überarbeitet wird."
---

Lade vor dem Schreiben den Skill `github-schreibstil` und befolge ihn. Er regelt Ton, Schreibung, den Hinweis auf den Agenten und was nicht in den Text gehört. Dieser Skill legt fest, was in ein Issue gehört und wie es aufgebaut ist.

Wer das Issue liest, soll verstehen, wie es gerade aussieht, warum das ein Problem ist und was getan werden soll, ohne vorher im Code oder in anderen Issues nachzulesen.

## Vorher Kontext sammeln

- Nach bestehenden Issues suchen (`gh issue list --search`), damit kein Duplikat entsteht. Gibt es schon eins, lieber dort kommentieren (Skill `pr-kommentieren`) oder das neue Issue darauf verlinken.
- Den Ist-Zustand prüfen, statt ihn aus dem Gedächtnis zu beschreiben: was kann die Anwendung heute, was fehlt, wo hakt es?
- Klären, an wen sich das Issue richtet und ob es zu einem größeren Thema gehört.

## Titel

Kurz und deutsch, benennt das Thema oder Ziel, zum Beispiel "Passwort selbst zurücksetzen". Keine Präfixe wie `bug:` oder `feat:`.

## Text

Nach dem Hinweis auf den Agenten kommen diese Teile, in dieser Reihenfolge. Überschriften klein und kurz, wie bei PRs.

1. **Kontext**, zwei bis vier Sätze ohne Überschrift: worum geht es, warum ist es jetzt dran und warum ist es wichtig. Richtet sich das Issue an eine Person, sprich sie mit ihrem Vornamen an. Wenn etwas erwartbar noch fehlt, sag das offen.
2. **offene punkte**: zwei bis fünf Stichpunkte zum Ist-Zustand, also was heute fehlt oder falsch läuft, aus Sicht dessen, der die Anwendung benutzt oder fachlich versteht ("ein vergessenes passwort kann nur der support zurücksetzen").
3. **todos**: zwei bis fünf Stichpunkte, was getan werden soll. Jeder Punkt ist eine Aufgabe, die man abhaken kann ("mail mit einem einmaligen link verschicken"). Was nur gemockt werden soll, ausdrücklich so sagen.
4. **offene fragen**: nur wenn etwas noch entschieden werden muss. Höchstens drei Stichpunkte.

Ein kleines Issue mit nur einem Punkt braucht keine Überschriften. Dann reichen Kontext und ein Satz dazu, was zu tun ist.

Das Ganze soll in unter einer Minute gelesen sein, also grob 150 Wörter ohne Titel. Längere Analysen, Rechtsgrundlagen oder Recherche gehören in einen Kommentar oder eine verlinkte Doku, nicht in den Issue-Text.

## Beispiel

```
Passwort selbst zurücksetzen

(geschrieben von jonas' agent)

Beim support landen gerade mehrmals pro woche anfragen, weil jemand sein passwort vergessen hat. Das kostet jedes mal zeit und der nutzer kommt so lange nicht rein, deshalb sollte das ohne support gehen.

offene punkte
- ein vergessenes passwort kann nur der support zurücksetzen.
- außer bei der registrierung verschickt die anwendung keine mails an nutzer.

todos
- link "passwort vergessen" auf der anmeldeseite einbauen.
- mail mit einem einmaligen link verschicken, der nach einer stunde abläuft.
- die mail erst mal nur auf deutsch, englisch kommt später.

offene fragen
- sollen nach dem zurücksetzen alle anderen sitzungen abgemeldet werden?
```
