---
name: pr-schreiben
description: "Schreibt Titel und Beschreibung eines GitHub Pull Requests in Jonas' Stil: deutsch, mit Kontext, warum es die Änderung gibt, und einer Übersicht, die auch ohne Fachwissen verständlich ist. Immer verwenden, wenn ein PR erstellt oder seine Beschreibung überarbeitet wird."
---

Lade vor dem Schreiben den Skill `github-schreibstil` und befolge ihn. Er regelt Ton, Schreibung, den Hinweis auf den Agenten und was nicht in den Text gehört. Dieser Skill legt fest, was in einen PR gehört und wie er aufgebaut ist.

Wer den PR liest, soll ohne Blick in den Code verstehen, worum es geht, warum es die Änderung gibt und was er jetzt tun muss.

## Vorher Kontext sammeln

- Commits und geänderte Dateien gegenüber dem Basis-Branch ansehen (`git log`, `git diff --stat`).
- Passende Issues suchen (`gh issue list`), vor allem solche, die der PR löst oder teilweise löst.
- Klären, ob der PR auf einem anderen PR aufbaut oder etwas vorher gemergt werden muss.
- Klären, was geprüft ist: laufen die Tests, wurde es von Hand ausprobiert, gab es ein Review?

## Titel

Ein kurzer deutscher Satzteil, der sagt, was danach geht oder anders ist, zum Beispiel "Nutzer können ihr Passwort selbst per Mail zurücksetzen". Keine Präfixe wie `feat(...)`, keine Klassen- oder Statusnamen.

## Beschreibung

Nach dem Hinweis auf den Agenten kommen diese Teile, in dieser Reihenfolge. Überschriften klein und kurz ("übersicht", "was sich ändert"), keine `##`-Blöcke für jeden Satz.

1. **Kontext**, ein bis drei Sätze ohne Überschrift: worum geht es und warum jetzt. Wenn es ein Issue dazu gibt, nenne es mit seinem Titel als Link.
2. **übersicht**: zwei bis vier Sätze Fließtext, die zusammenfassen, was gemacht wurde. Geschrieben für jemanden, der sich im Thema nicht auskennt: erst in einem Satz erklären, worum es fachlich geht, dann sagen, was die Anwendung jetzt anders macht. Keine Fachdetails, keine Aufzählung.
3. **was sich ändert**: drei bis fünf Stichpunkte, jeder ein einfacher ganzer Satz mit höchstens etwa zwanzig Wörtern aus Sicht dessen, der die Anwendung benutzt oder fachlich versteht ("nach dem zurücksetzen werden alle anderen sitzungen abgemeldet"), nicht aus Sicht des Codes. Hier stehen die konkreten Punkte, die in der Übersicht fehlen. Zusammenfassen statt jeden Commit aufzählen.
4. **was noch offen ist**: nur wenn bewusst etwas fehlt oder nur gemockt ist. Höchstens drei ebenso kurze Stichpunkte.
5. **zum reviewen**: ein bis drei Sätze. Was der Reviewer tun soll, ob etwas vorher gemergt werden muss, wo er am besten anfängt, und wie es um Tests steht ("alle tests laufen durch", "noch nicht von hand getestet").

Danach, falls der PR ein Issue schließt, eine Zeile `Closes <volle Issue-URL>`.

Das Ganze soll in gut einer Minute gelesen sein, also grob 200 Wörter ohne Titel.

## Beispiel

```
Nutzer können ihr Passwort selbst per Mail zurücksetzen

(geschrieben von jonas' agent)

Bisher musste der support jedes vergessene passwort von hand zurücksetzen, zuletzt mehrmals pro woche. Das ist ein teil von [Weniger Supportanfragen beim Login](https://github.com/beispiel/app/issues/12).

übersicht
Wer sein passwort vergisst, kann sich jetzt selbst helfen. Auf der anmeldeseite gibt es einen link, über den man eine mail mit einem einmaligen link bekommt, und darüber legt man ein neues passwort fest. Der support muss dafür nichts mehr tun.

was sich ändert
- auf der anmeldeseite gibt es den link "passwort vergessen".
- der link in der mail gilt eine stunde und nur für ein einziges zurücksetzen.
- nach dem zurücksetzen werden alle anderen sitzungen abgemeldet.

was noch offen ist
- die mail gibt es bisher nur auf deutsch, englisch kommt später.

zum reviewen
Am besten mit dem versand der mail anfangen, da steckt die meiste logik. Alle tests laufen durch, von hand habe ich es lokal mit einer testadresse ausprobiert.
```
