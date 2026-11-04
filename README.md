# private-skills

Jonas' eigene Skills für Claude Code. Jeder Ordner ist ein Skill.

Die Skills trennen Inhalt und Ausdruck. Stil-Skills regeln, wie ein Text klingt, die übrigen legen fest, was hineingehört, und laden dafür den passenden Stil-Skill.

| Skill | Art | Wofür |
|---|---|---|
| `jonas-writing-style` | Stil | Grundlage für alle Texte, die andere lesen, auf Englisch und Deutsch |
| `natural-german-2` | Stil | Natürlich klingendes Deutsch, wird von `jonas-writing-style` geladen |
| `github-schreibstil` | Stil | Agenten-Hinweis, Schreibung und Bilder für GitHub-Texte ans Team, baut auf `jonas-writing-style` auf |
| `commit-schreiben` | Inhalt | Commit-Messages |
| `pr-schreiben` | Inhalt | Titel und Beschreibung eines Pull Requests |
| `pr-kommentieren` | Inhalt | Kurzer Kommentar an Teamkollegen auf PRs oder Issues |
| `issue-schreiben` | Inhalt | Titel und Text eines Issues |
| `lernskript-schreiben` | Inhalt | Lernskript als LaTeX-Dokument und PDF |

## Einrichten

Claude Code lädt persönliche Skills aus `~/.claude/skills/`. Am einfachsten klonst du das Repo einmal und verlinkst jeden Ordner dorthin. Dann reicht später ein `git pull`, und die nächste Session hat den neuen Stand.

```bash
git clone https://github.com/Buecherfresser/private-skills ~/Development/private-skills
mkdir -p ~/.claude/skills
for d in ~/Development/private-skills/*/; do ln -sfn "${d%/}" ~/.claude/skills/"$(basename "$d")"; done
```

Liegt in `~/.claude/skills/` schon ein echter Ordner mit demselben Namen, lösch ihn vorher, sonst landet der Link darin. Kommt ein neuer Skill dazu, die Schleife einfach noch mal laufen lassen.
