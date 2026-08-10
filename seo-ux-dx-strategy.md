# SEO-, User- & Developer-Friendliness-Strategie für jaksam-docs

Interne Planungsnotiz, kein Teil der veröffentlichten Doku (nicht in `docs.json`-Nav eingebunden). Grundlage: Analyse des Repos nach Abschluss der GitBook→Mintlify-Migration (17 Module, ~350 Seiten).

## Warum das ein Zielkonflikt ist

Die drei Ziele wollen strukturell unterschiedliche Dinge:

| Ziel | Will... |
|---|---|
| **SEO** | Wenige, eindeutige, keyword-starke Seiten mit einzigartigem Title/Description; starke interne Verlinkung; keine Duplicate-Content-Signale |
| **User-Friendliness** (Server-Owner, oft nicht technisch) | Pro Produkt in sich geschlossene Anleitungen, die man lesen kann ohne zwischen Seiten zu springen — auch wenn sich Inhalte zwischen Produkten wiederholen |
| **Developer-Friendliness** (Leute, die Exports/Events integrieren) | Möglichst viele, sehr kurze, tief verlinkbare Einzelseiten (1 Export = 1 URL) zum Scannen und Copy-Pasten |

DX will viele dünne Seiten, SEO mag dünne Seiten eigentlich nicht, UX will Wiederholung, SEO bestraft Wiederholung. Die Lösung ist nicht "eins gewinnt", sondern die Reibung an den richtigen Stellen wegzunehmen.

## Ist-Zustand (aus der Migration bekannt)

- **351 Content-Seiten**, alle jetzt mit Frontmatter (`title`, `description`, `icon`)
- **URL-Struktur** ist bereits ordentlich: `/modul-name/seiten-slug`, sprechend, flach genug
- **15 Produkte**, jedes mit fast identischem Seiten-Set: `home`, `installation`, `faq`, `client/*`, `server/*`
- **Reference-Seiten** (1 Export/Event pro Seite) sind absichtlich sehr kurz — das ist DX-Pattern, kein Bug
- **Kein `redirects`-Feld in `docs.json`**, kein `robots.txt`/`sitemap.xml`/`CNAME` im Repo gefunden
- **`index.mdx`** (die wichtigste SEO-Seite, weil Root-Domain) verlinkt aktuell nur auf allgemeine Hilfe-Seiten (Update, Troubleshooting, FAQ, Nexus-Terms) — **keines der 15 Produkte wird von der Startseite aus verlinkt oder überhaupt erwähnt**
- Viele `installation.md`-Seiten teilen sich Wort für Wort denselben Absatz (FileZilla-Warnung, "You are ready to go! Enjoy the script 😁") — bewusste Wiederholung für UX, aber technisch Duplicate Content

## Konkrete Empfehlungen

### 1. Redirects einrichten — höchste Priorität, bevor der PR live geht

Die GitBook-URLs (`documentation.jaksam-scripts.com/...`) sind vermutlich seit Jahren indexiert und in Foren/Tebex-Beschreibungen verlinkt. Mintlify unterstützt einen `"redirects"`-Block in `docs.json` (`{"source": "/old-path", "destination": "/new-path"}`). Ohne das:

- verliert jede alte URL ihren Google-Rank beim nächsten Crawl (404 oder neue URL ohne Linkjuice)
- alle externen Backlinks (Forenposts, alte Support-Tickets) laufen ins Leere

**Aktion:** Alte GitBook-Pfade sammeln (aus Sitemap/Google Search Console falls Zugriff vorhanden) und als `redirects` in `docs.json` mappen, bevor gemerged wird.

### 2. Startseite (`index.mdx`) zur echten Produktübersicht machen

Aktuell keine Produktliste auf der Root-Seite = die wichtigste SEO-Seite der ganzen Domain verschenkt ihr Ranking-Potenzial für Keywords wie "jaksam jobs creator doku" etc., und neue Besucher, die über Google direkt auf die Startseite kommen, sehen nicht, was es überhaupt gibt.

**Vorschlag:** Eine `<CardGroup>` mit allen 15 Produkten (Icon, 1 Satz Beschreibung, Link zur jeweiligen `home`-Seite) oberhalb der bestehenden "How to use"-Sektion.

### 3. Eindeutigere `<title>`-Tags für gleichnamige Seiten

15× `title: "Installation"` erzeugen 15 URLs mit technisch identischem Seitentitel (sofern Mintlify den Titel nicht automatisch mit dem Gruppennamen präfixt — das müsste im Rendering geprüft werden). Für Suchmaschinen-Snippets ist das schlecht unterscheidbar.

**Vorschlag:** `description` bleibt produktspezifisch (ist es bereits durch die Migration), aber prüfen ob der gerenderte `<title>`-Tag automatisch "Installation – Jobs Creator" wird. Falls nicht, den Produktnamen explizit in die Description aufnehmen (SEO-Snippet-Text) statt im `title`.

### 4. Duplicate Content bei Installation/Danger-Blöcken entschärfen, ohne UX zu verlieren

Nicht zusammenlegen (siehe letzte Diskussion — eigenständige Produkte). Stattdessen:

- Die identischen Blöcke (FileZilla-Warnung, "Enjoy the script") sind kurz genug, dass Google sie i. d. R. nicht als Duplicate-Content-Problem wertet — das eigentliche Risiko sind eher **komplette Seiten**, die sich zu >90 % gleichen (z. B. Notification-Replace-Seiten, die sich nur im Skriptnamen unterscheiden)
- Diese Reference-artigen Seiten sind aber DX-Pattern (Copy-Paste-Baustein) — hier zieht SEO gegenüber DX klar den Kürzeren, und das ist okay, weil diese Seiten selten die Haupt-Einstiegspunkte aus Google sind (Leute suchen nicht nach "replace default notifications", sondern landen darauf über interne Links/Doku-Suche)

### 5. Interne Verlinkung zwischen verwandten Produkten ausbauen

`jaksams-scripts/common-faq.md` als zentraler Hub existiert schon — gut. Ausbaufähig: Produkte, die oft zusammen gekauft werden (z. B. Vehicles Keys ↔ Dealerships Creator, Doors Creator ↔ Easy Allowlist als "Server-Security-Paket"), könnten sich in ihren `home.md`-Seiten gegenseitig per Card verlinken. Stärkt SEO (Linkjuice-Verteilung) und User-Friendliness (Entdeckbarkeit) gleichzeitig, kostet nichts an DX.

### 6. Reference-Seiten: Mindest-Content-Schwelle für Kontext

Aktuelle Reference-Seiten (z. B. `get-queue-count.md`) sind so kurz wie nötig — das ist richtig für DX. SEO-technisch schadet das kaum, weil diese Seiten selten Google-Einstiegspunkte sind. Kein Handlungsbedarf, nur nicht künstlich aufblähen ("SEO-Text" auf Reference-Seiten wäre DX-schädlich).

### 7. OpenGraph/Social-Preview prüfen

Für Foren-Links (FiveM-Forum-Posts verlinken oft auf einzelne Doku-Seiten) lohnt sich ein Check, ob Mintlify automatisch OG-Tags aus `title`/`description`/`logo` generiert, oder ob pro Produkt ein eigenes OG-Bild sinnvoll wäre (aktuell nur 1 globales `logo.png` in `docs.json`).

## Priorisierte Reihenfolge

1. **Redirects** (verhindert SEO-Schaden durch den Umzug selbst — zeitkritisch vor Merge)
2. **Startseite mit Produktübersicht** (größter Hebel, kleinster Aufwand)
3. Interne Cross-Links zwischen verwandten Produkten
4. Title/Description-Feinschliff für Duplikat-Titel
5. OG-Tags/Social-Preview (nice-to-have, kein Blocker)

Punkt 6 (Reference-Seiten) bewusst **kein** Punkt auf der Liste — dort ist der Ist-Zustand bereits der richtige Trade-off für DX.
