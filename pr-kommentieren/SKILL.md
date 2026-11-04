---
name: pr-kommentieren
description: Write a short GitHub PR or issue comment on Jonas's behalf, addressed to a teammate by first name and marked as written by his agent. Two kinds - a status update (what changed, what to do, where it stands) or a finding (one concrete case with numbers and a link to the spot, no request). Use whenever posting a comment to a teammate on a pull request or issue.
---

Lade vor dem Schreiben den Skill `github-schreibstil` und befolge ihn. Er regelt zusammen mit `jonas-writing-style` Sprache, Ton, Schreibung, den Hinweis auf den Agenten und was nicht in den Text gehört. Dieser Skill legt fest, was in einen Kommentar gehört.

Jeder Kommentar richtet sich an eine Person und spricht sie mit ihrem Vornamen an. Er ist eine von zwei Arten.

## Stand melden

Du hast etwas umgesetzt oder weitergebracht und sagst der Person Bescheid.

- Höchstens drei Sätze.
- Je ein kurzer Satz dazu, was sich geändert hat, was die Person tun soll und wo die Sache gerade steht. Kein Satz zu jedem einzelnen Schritt oder Fix.

## Befund schildern

Dir ist im Code, in einem Test oder in einer Ausgabe der Person etwas aufgefallen, etwa im Review.

- Der erste Satz sagt, was schiefläuft, in Alltagssprache.
- Danach der Fall selbst, mit echten Zahlen: was hineingeht, was herauskommt und was herauskommen müsste. Bei mehreren Fällen eine kleine Tabelle.
- Die Stelle im Code verlinken (Permalink, siehe `github-schreibstil`). Zeigt ein Test oder ein Beispiel denselben Fehler, auch ihn nennen und sagen, warum er ihn nicht bemerkt.
- Keine Aufforderung und kein Lösungsvorschlag ("kannst du ..."). Wie die Person den Befund löst, entscheidet sie.
- Kurze Absätze statt einer langen Satzkette. Ein Befund je Kommentar.

## Beispiele

```
(geschrieben von jonas' agent)

Hey anna, man kann sein passwort jetzt selbst auf der anmeldeseite zurücksetzen, der support muss das also nicht mehr von hand machen. Kannst du es einmal mit deinem testkonto ausprobieren und auf den text der mail schauen? Alles ist gemergt, nur die englische fassung der mail fehlt noch.
```

```
(geschrieben von jonas' agent)

Hey elias, bei einem inklusivtarif wandert der gesamtpreis mit dem netzentgelt mit, obwohl er vereinbart ist.

In der demo-rechnung 07 steigt das netzentgelt zum 01.07.2025 von 8,20 auf 8,60 ct, der energieanteil bleibt bei 15,20 ct, und der gesamtpreis steigt so von 29,691 auf 30,091 ct je kWh, ohne angekündigte preisänderung.

Die tests bemerken das nicht, weil die [nachrechnung](https://github.com/ekviso/Omnigy-ERP/blob/b7a6ce9dc394135815f4ff76b62e6ed607c19aff/anwendung/src/test/java/de/evu/erp/abrechnung/Rechnungsnachrechnung.java#L276-L277) den erwarteten gesamtpreis ebenfalls als summe der bestandteile bildet.
```
