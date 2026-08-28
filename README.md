# Handoff: vonvorteil.de — Website-Refresh

## Overview

Neuer digitaler Auftritt für **VonVorteil** (Employer-Branding-Beratung, München, inhabergeführt von Jörg Schleburg). Der Entwurf ist bewusst radikal reduziert: keine klassische Navigation, kein Logo im Header, eine durchgehende Farbfläche, Typografie als tragendes Gestaltungsmittel. Die Wirkung entsteht aus Größenverhältnissen, Weißraum und Scroll-Rhythmus, nicht aus Bildmaterial.

Zwei Zugänge statt einer Navigation:

- **Für Menschen** — die Startseite: wenige Module, große Aussagen, souveräner erster Eindruck.
- **Für KI** — ein maschinen- und SEO-orientierter Hub mit strukturierten Inhalten, Definitionen, FAQ und thematischen Clustern. Ziel: Zitierfähigkeit in KI-Systemen und klassische Auffindbarkeit.

## About the Design Files

Die Dateien in `prototype/` sind **Design-Referenzen in HTML** — Prototypen, die Aussehen und Verhalten zeigen. Sie sind **kein Produktionscode zum direkten Übernehmen**. Sie wurden aus einer Streaming-Komponenten-Umgebung heraus zu eigenständigen HTML-Dateien gebündelt; Bilder und Schriften sind als Data-URLs eingebettet, das Markup ist maschinengeneriert und für Produktion nicht geeignet.

Aufgabe: die Designs im Ziel-Stack **nachbauen** — mit dessen bestehenden Mustern und Bibliotheken. Wenn noch kein Stack existiert, ist für dieses Projekt **Astro** oder **Next.js (App Router)** mit statischem Export die naheliegende Wahl: die Seite ist inhaltsgetrieben, braucht SEO/SSG, einen Blog aus Markdown/CMS und nur wenige Interaktionen.

Öffnen Sie zum Ansehen `prototype/index.html` direkt im Browser.

**Wichtig:** Der Prototyp enthält den mobilen Hero (vierzeilig, maximale Schrift an „Employer“, 18px Seitenrand unter ~710px). Desktop bleibt dreizeilig.

## Fidelity

**High-fidelity.** Farben, Schriftgrößen, Abstände und Animationen sind final gedacht und exakt dokumentiert. Der Nachbau soll pixelgenau erfolgen. Alle Texte sind Endtexte und stammen 1:1 aus der bestehenden Website bzw. wurden vom Kunden freigegeben — **Copy nicht umformulieren**.

---

## Design Tokens

### Farben

| Token | Hex | Verwendung |
| --- | --- | --- |
| Petrol (Fläche) | `#123430` | Hintergrund der gesamten Seite, ausnahmslos |
| Reispapier (Schrift) | `#F6F2E8` | Primäre Schriftfarbe auf Petrol |
| Orange (Akzent) | `#FF5A1F` | Claim-Headline, E-Mail-Adresse, Link-Hover, Newsletter-Button |
| Tinte | `#12211F` | Standard-Linkfarbe im Reset (kommt auf der Seite kaum vor) |
| Reispapier 88 % | `rgba(246,242,232,0.88)` | Fließtext im Statement-Modul |
| Reispapier 68 % | `rgba(246,242,232,0.68)` | Footer-Text |
| Reispapier 55 % | `rgba(246,242,232,0.55)` | Nav-Labels (Ruhezustand), Hinweiszeile Newsletter |
| Reispapier 50 % | `rgba(246,242,232,0.5)` | Datumszeilen im Wissens-Modul |
| Reispapier 35 % | `rgba(246,242,232,0.35)` | Unterstrich des Newsletter-Eingabefelds |
| Reispapier 18 % | `rgba(246,242,232,0.18)` | Trennlinien im Wissens-Modul |

Es gibt **genau eine Flächenfarbe**. Kein Hell-Dunkel-Wechsel zwischen Sektionen, keine Gradienten (Ausnahme: keine).

### Typografie

**Rubik** (Google Fonts), Gewichte 400/500/600/700/800/900.
`@import url('https://fonts.googleapis.com/css2?family=Rubik:wght@400;500;600;700;800;900&display=swap')`

Globale Regeln:

```css
body { margin:0; background:#123430; font-family:"Rubik",Helvetica,Arial,sans-serif; -webkit-font-smoothing:antialiased }
h1,h2,h3 { font-family:"Rubik",sans-serif }
h1,h2 { text-transform:uppercase; letter-spacing:-0.012em }
a { color:#12211F; text-decoration:none }
a:hover { color:#FF5A1F }
```

Typo-Skala (alle Display-Größen mit `font-weight:900`):

| Rolle | font-size | line-height | letter-spacing |
| --- | --- | --- | --- |
| Hero H1 | `clamp(64px,12.4vw,250px)` | `0.79` | `-0.055em` |
| Kundenname (Zeile) | `clamp(44px,10.6vw,190px)` | `0.92` | `-0.05em` |
| Claim H2 („IQ ist VonVorteil.") | `clamp(48px,10vw,190px)` | `0.86` | `-0.05em` |
| Kontakt H2 („Sprechen wir.") | `clamp(44px,8.6vw,168px)` | `0.88` | `-0.05em` |
| Telefonnummer | `clamp(30px,5.4vw,104px)` | `1` | `-0.05em` |
| E-Mail-Adresse | `clamp(26px,4.4vw,84px)` | `1` | `-0.045em` |
| Blog-Titel | `clamp(26px,4.4vw,76px)` | `0.94` | `-0.045em` |
| Newsletter H2 | `clamp(34px,6.2vw,120px)` | `0.92` | `-0.05em` |
| Statement-Fließtext | `clamp(26px,3.1vw,52px)`, `500` | `1.28` | `-0.015em` |
| Newsletter-Bestätigung | `clamp(22px,2.6vw,42px)`, `500` | `1.3` | `-0.015em` |
| Newsletter-Input | `clamp(20px,2.4vw,34px)`, `600` | — | `-0.02em` |
| Nav-Label vertikal | `17px`, `700` | — | `0.08em` |
| Datumszeile | `14px`, `600` | — | — |
| Footer-Links | `14px` | — | — |
| Kleingedrucktes | `15px` | `1.5` | — |

Textspalten sind über `max-width` in `ch` begrenzt: Claim `16ch`, Statement-Text `30ch`, Kontakt-H2 `18ch`, Blog-Titel `26ch`, Newsletter-H2 `20ch`, Hinweiszeile `44ch`.

### Abstände

Sektionen arbeiten mit Viewport-Einheiten statt fixer Pixel: `padding: 14vh 40px` als Regelfall, Hero `12vh 40px`, Wissen `14vh 40px 10vh`, Newsletter `14vh 40px 12vh`, Logo-Block `96px 40px 80px`, Footer `56px 40px`. Horizontal überall **40px**. Innerhalb von Sektionen: `gap` 48–64px, Kontaktzeilen `gap:20px`, Blog-Einträge `padding:32px 0`.

### Radien, Rahmen, Schatten

- Radius **0** überall — **eine Ausnahme:** Newsletter-Button `border-radius:999px`.
- Keine Schatten. Keine Karten. Keine Boxen.
- Rahmen nur als 1px-Haarlinien in `rgba(246,242,232,0.18)` (Blog-Trenner) und 2px-Unterstrich am Eingabefeld.

---

## Screens / Views

### 1. Startseite (`prototype/index.html`)

Wrapper: `<div style="background:#123430;color:#F6F2E8;overflow-x:hidden">`. Alle Module liegen darin, Reihenfolge wie unten.

#### 1.1 Hero

- `position:sticky; top:0; z-index:0; height:100vh; overflow:hidden; display:flex; flex-direction:column; justify-content:center; padding:12vh 40px`
- **Sticky ist konstitutiv:** das folgende Modul schiebt sich über den stehenden Hero.
- **Vertikale Navigation** oben rechts: `position:absolute; top:44px; right:34px; z-index:30`, Flex-Spalte, `align-items:flex-end`, `gap:22px`. Beide Labels `writing-mode:vertical-rl`, `17px/700`, `letter-spacing:0.08em`, Ruhefarbe `rgba(246,242,232,0.55)`, Hover `#F6F2E8`. Labels: „Für Menschen" (aktuelle Seite, kein Link), „Für KI" (Link auf den KI-Hub).
- **H1 mit Porträt-Füllung** — der zentrale Effekt der Seite:

```css
font-size: clamp(64px,12.4vw,250px);
font-weight: 900;
line-height: 0.79;
letter-spacing: -0.055em;
color: #F6F2E8;                        /* Fallback */
background-image: url(joerg-schleburg.png);
background-size: cover;
background-position: 50% 40%;          /* Handy: Augen in EMPLOYER; Desktop setzt 43% via JS */
background-repeat: no-repeat;
-webkit-background-clip: text;
background-clip: text;
-webkit-text-fill-color: transparent;
```

Text: `Die Employer<br />Branding<br />Agentur` auf Desktop (drei Zeilen). Unter ~710px vierzeilig: `Die / Employer / Branding / Agentur`.
Das Bild ist **unbehandelt** — kein Helligkeits-, Kontrast- oder Sättigungsfilter, keine Overlays. Wichtig, das wurde mehrfach korrigiert.
Fallback ohne `background-clip:text`-Support: Schrift in `#F6F2E8`, Bild unsichtbar.

#### 1.2 Kundenliste

- `position:relative; z-index:2; margin-top:-14vh; padding:0 0 96px`
- `clip-path: polygon(0 14vh, 100% 0, 100% 100%, 0 100%)` — die diagonale Oberkante schneidet in den Hero; im Scroll wird der vh-Wert animiert von 30vh auf 0 (siehe Interaktionen).
- Ein Spacer `height:22vh` vor der ersten Zeile.
- 17 Zeilen, je `div[data-client-row]` mit `padding:0 40px; will-change:transform`, darin ein `span`: `display:block; padding:26px 0; font-size:clamp(44px,10.6vw,190px); font-weight:900; line-height:0.92; letter-spacing:-0.05em; text-transform:uppercase`.
- Reihenfolge (exakt): Bechtle · BSH · Caritas · Dyson · Miele · KUKA · Retterspitz · Lotto Bayern · Ingram Micro · Avery Zweckform · Kraftanlagen Energies & Services SE · Hannover Re · Ecovis · Bergzeit · Brand · u. v. m.
- Keine Überschrift, keine Trennlinien, keine Logos.

#### 1.3 Statement („IQ ist VonVorteil.")

- `min-height:100vh; display:flex; flex-direction:column; justify-content:center; gap:56px; padding:14vh 40px`
- H2 in **Orange** `#FF5A1F`: „IQ ist VonVorteil."
- Absatz, `max-width:30ch`, Farbe `rgba(246,242,232,0.88)`, `text-wrap:pretty`:

> Belastbare Daten. Ein geschulter Blick für das Besondere. Über Jahre aufgebaut, beides.
> So entsteht ein Bild von Ihnen, das trägt – und Entscheidungen, die halten.

#### 1.4 Kontakt (`id="kontakt"`)

- `min-height:100vh; display:flex; flex-direction:column; justify-content:center; gap:64px; padding:14vh 40px`
- H2 „Sprechen wir." — **jeder Buchstabe ein eigenes `<span>`** mit `display:inline-block`, `transform-origin:50% 100%` und gestaffelter Animation (siehe Interaktionen). Das Leerzeichen ist ein `span` mit `width:0.26em`.
- Darunter Flex-Spalte, `gap:20px`, `align-items:flex-start`:
  - `<a href="mailto:schleburg@vonvorteil.de">` in Orange
  - `<a href="tel:017621643173">0176 21643173</a>` in Reispapier
- Keine Buttons, kein Formular, keine Verknappung.

#### 1.5 Wissen (drei aktuellste Beiträge)

- `padding:14vh 40px 10vh`, Flex-Spalte.
- Drei Links, je `display:block; padding:32px 0; border-top:1px solid rgba(246,242,232,0.18)`; der letzte zusätzlich `border-bottom`. Hover: Textfarbe → `#FF5A1F`.
- Aufbau pro Eintrag: Datumszeile (`14px/600`, `rgba(246,242,232,0.5)`, `margin-bottom:12px`), darunter der Titel.
- Inhalte:
  - 12.03.2026 — Employer Branding ohne Agentur. Geht das?
  - 30.01.2026 — Anja Förster, wie gelingt Wandel, wenn niemand kommt, um uns zu retten?
  - 16.01.2026 — Wolf Lotter, was bedeutet es eigentlich, digital erwachsen zu sein?
- Keine Überschrift über dem Modul, kein „mehr lesen".

#### 1.6 Newsletter

- `padding:14vh 40px 12vh; display:flex; flex-direction:column; gap:48px`
- H2: „Einmal im Monat ein Gedanke, der bleibt."
- Formularzeile: Flex, `flex-wrap:wrap`, `gap:20px`, `max-width:900px`.
  - `input[type=email]`, Placeholder „Ihre E-Mail-Adresse": `flex:1 1 340px; padding:20px 4px; background:transparent; border:0; border-bottom:2px solid rgba(246,242,232,0.35); outline:none`.
  - Button „Anmelden": `padding:20px 34px; background:#FF5A1F; color:#123430; border:0; border-radius:999px; 17px/800`. Hover: `background:#F6F2E8`.
- Hinweiszeile darunter, `15px`, `max-width:44ch`: „Kein Verkauf, keine Weitergabe der Adresse. Abmeldung jederzeit mit einem Klick."
- Nach Absenden ersetzt eine Zeile in Orange das Formular: „Danke. Sie erhalten eine Bestätigung per Mail."

#### 1.7 Logo-Block

`padding:96px 40px 80px`, zentriert, Container `width:clamp(86px,9.6vw,144px)`, darin `vonvorteil_logo.png` (`width:100%; height:auto; display:block`). Das Logo erscheint **nur hier** — nicht im Header. Es wird nie umgefärbt oder beschnitten.

#### 1.8 Footer

`padding:56px 40px`, Flex, `flex-wrap:wrap`, `gap:24px`, `justify-content:space-between`. Links: Wortmarke „VonVorteil" (`17px/800`, `letter-spacing:-0.03em`, `#F6F2E8`). Rechts: Linkgruppe `gap:24px`, `14px` — Kontakt (Anker `#kontakt`), Impressum, Datenschutz, AGB. Farbe geerbt (`rgba(246,242,232,0.68)`), Hover Orange.

### 2. Für KI (`prototype/fuer-ki.html`)

Der maschinenlesbare Zugang. Gleiche Farbfläche und Schrift, aber bewusst nüchterner: dichtere Typo, klare Hierarchie aus H1/H2/H3, Definitionslisten, FAQ-Blöcke, Themencluster mit internen Verlinkungen. Zweck: strukturierte, zitierfähige Substanz für Suchmaschinen und KI-Systeme — inhaltliche Tiefe, die die Startseite absichtlich nicht zeigt („vorne reduziert, hinten tief").

Beim Nachbau relevant: Diese Seite braucht echtes semantisches Markup (`<article>`, `<section>`, `<dl>`, korrekte Heading-Reihenfolge), JSON-LD (`Organization`, `Person`, `FAQPage`, `Article`), sowie `llms.txt` und Sitemap. Das ist Geschäftsziel, nicht Beiwerk.

### 3. Cluster-Seite (`prototype/fuer-ki-beratung.html`)

Muster für die Themencluster unterhalb des KI-Hubs (Beispiel: Employer-Branding-Beratung). Als Vorlage für die weiteren Cluster gedacht: Employer Branding, Employer-Branding-Agentur, Arbeitgeberpositionierung, EVP, Employer-Branding-Strategie, Kampagnen, Karriereseiten, Arbeitgeberkommunikation, Workshops.

### 4. Blog-Übersicht (`prototype/blog.html`)

Chronologische Liste aller Beiträge in derselben Typo-Logik wie das Wissens-Modul der Startseite: Datum klein darüber, Titel groß, Haarlinie als Trenner, Hover in Orange. Keine Teaser-Bilder, keine Kacheln.

### 5. Artikelvorlage (`prototype/artikel.html`)

Lesevorlage für einen einzelnen Beitrag: große Titelzeile, Metazeile, Fließtextspalte mit begrenzter Zeilenlänge. Die Bestandsartikel der alten Website sollen hierher migriert werden (URLs möglichst erhalten oder per 301 umleiten — die Beiträge tragen Suchwert).

---

## Interactions & Behavior

Alle Scroll-Effekte hängen an **einem** Scroll-Handler, der auf ~60 fps gedrosselt ist (16 ms) und direkt im Handler rechnet — kein `requestAnimationFrame`-Loop (der pausiert in inaktiven Tabs und friert die Effekte im Startzustand ein; das war ein echter Bug). Der Handler wird zusätzlich einmal beim Mount ausgeführt, damit die Startwerte stimmen.

Berechnungen pro Frame:

1. **Hero-Porträt-Parallaxe** (`[data-parallax-bg]`, Attribut `data-parallax-bg="1.1"`, `data-bg-base` 40 Handy / 43 Desktop, gesetzt in `fitHero`):
   Fortschritt `p = clamp((rect.top + rect.height/2 − vh/2) / vh, −1, 1)`, dann
   `backgroundPositionY = (base + p · speed · 34)%`, gerundet auf 0,5 % (Schreibvorgänge sparen).
2. **Diagonale Überschiebung** der Kundenliste: `u = clamp((vh − rect.top) / (vh·0.9), 0, 1)`, geglättet mit `e = u²(3−2u)`, daraus
   `clip-path: polygon(0 ((1−e)·30)vh, 100% 0, 100% 100%, 0 100%)`.
3. **Kundenzeilen**, je Zeile: `k = clamp((vh − rect.top) / (vh·0.55), 0, 1)`, auf 1/50 gerundet, dann
   `transform: translate3d(((1−k)·90)px,0,0)`, `opacity: 0.15 + 0.85·k`.
   Die Zeilen laufen also einzeln von rechts ein und werden dabei dichter.
4. **Generische Parallaxe** (`[data-parallax]`): `translate3d(0, p·speed·−120px, 0)`.
5. **Zoom-Drift** eines Sektionsbildes (`[data-claim-photo]`): `scale` von 1,1 auf 1,44 über den Scrollverlauf, dazu vertikaler Versatz.

Wichtig beim Nachbau: **kein `transform` auf dem Element mit `background-clip:text`** — das bricht die Bildfüllung. Deshalb wird beim Hero ausschließlich `background-position-y` animiert.

**Sprech-Animation „Sprechen wir."** — CSS-Keyframes, Endlosschleife 3,4 s, Buchstaben gestaffelt (0 s, 0,05 s, … 0,55 s), der Punkt 0,6 s:

```css
@keyframes vv-say {
  0%,58%,100% { transform: translateY(0) scaleY(1) }
  64%  { transform: translateY(-0.055em) scaleY(1.07) }
  72%  { transform: translateY(0.03em) scaleY(0.93) }
  80%  { transform: translateY(0) scaleY(1) }
}
@keyframes vv-dot {
  0%,60%,100% { transform: scale(1); opacity: 1 }
  70% { transform: scale(1.35); opacity: 0.7 }
  82% { transform: scale(1); opacity: 1 }
}
```

Die Silben heben und stauchen sich nacheinander, dann 2 s Ruhe. Bitte `prefers-reduced-motion: reduce` respektieren und dann alle Scroll- und Sprech-Animationen deaktivieren.

**Hover-Zustände:** Links wechseln auf `#FF5A1F`; Nav-Labels von 55 % auf 100 % Deckkraft; Newsletter-Button von Orange auf Reispapier (Schrift bleibt Petrol); Blog-Einträge komplett auf Orange. Keine Unterstreichungen, keine Transform-Effekte.

**Responsive:** Ein einspaltiges Layout über alle Breiten; Größen skalieren über `clamp()` mit `vw`. Der Hero hat Media Queries unter ~710px: vierzeilige Headline, 18px Seitenrand, Schrift so groß wie das Wort „Employer“ in der verfügbaren Breite (und der Viewport-Höhe) zulässt.

## State Management

Sehr wenig Zustand:

- `nlMail` — Inhalt des Newsletter-Felds (Controlled Input).
- `nlDone` — Boolean; nach Absenden Formular ausblenden, Dankeszeile zeigen. Im Prototyp rein clientseitig, ohne Backend.
- Scroll-Fortschritte sind **kein** State: sie werden direkt in Style-Eigenschaften geschrieben, mit Vergleich gegen den letzten Wert, um Layout-Thrashing zu vermeiden.

Für die Produktion zusätzlich nötig: Newsletter-Anbindung (Double-Opt-in, DSGVO-konform), Formular-/Fehlerzustände am Eingabefeld, Blog-Daten aus CMS oder Markdown.

## Assets

| Datei | Herkunft | Verwendung |
| --- | --- | --- |
| `assets/joerg-schleburg.png` | vom Kunden geliefert | Porträt-Füllung der Hero-Headline, Augen in EMPLOYER (`50% 40%` Handy, `50% 43%` Desktop) |
| `assets/vonvorteil_logo.png` | vom Kunden geliefert | Logo-Block über dem Footer, unverändert verwenden |

Schrift: **Rubik** via Google Fonts (SIL Open Font License). Für die Produktion selbst hosten (WOFF2, `font-display:swap`) — das vermeidet den externen Request und ist datenschutzseitig sauberer. Benötigte Gewichte: 400, 500, 600, 700, 800, 900.

Keine Icons, keine Illustrationen, keine Emoji. Für „mehr"-Verweise ausschließlich `→` und `↗`.

## Files

```
prototype/index.html             Startseite (Hauptreferenz)
prototype/fuer-ki.html           KI-/SEO-Hub
prototype/fuer-ki-beratung.html  Cluster-Muster
prototype/blog.html              Blog-Übersicht
prototype/artikel.html           Artikelvorlage
assets/joerg-schleburg.png       Porträt
assets/vonvorteil_logo.png       Logo
```

Die HTML-Dateien sind eigenständig (Assets als Data-URLs eingebettet) und funktionieren offline. Die Assets liegen zusätzlich separat bei, weil die eingebetteten Varianten für den Nachbau unbrauchbar sind.

## Offene Punkte

1. **Mobiler Hero.** Im Prototyp umgesetzt: unter ~710px vierzeilige Headline, 18px Seitenrand, Schriftgröße per Messung an „Employer“ (so groß wie möglich, begrenzt durch Breite und Höhe). Desktop bleibt dreizeilig mit `clamp(64px,12.4vw,250px)`.
2. **Rechtstexte** — Impressum, Datenschutz, AGB sind verlinkt, aber nicht geschrieben.
3. **Weitere Cluster-Seiten** nach dem Muster von `fuer-ki-beratung.html`.
4. **`llms.txt`, `robots.txt`, `sitemap.xml`, JSON-LD** — noch nicht angelegt, gehören aber zum Kern des Auftrags (Auffindbarkeit ist erklärtes Hauptziel).
5. **Blog-Migration** — die Beiträge der alten Website übernehmen, URL-Struktur und Weiterleitungen klären.
6. **Newsletter-Backend** und Double-Opt-in.
7. **WhatsApp als Kontaktkanal** war im Briefing gewünscht, ist im Entwurf noch nicht umgesetzt.

## Haltung (bitte beim Nachbau mitdenken)

Der Entwurf lebt von Weglassen. Bei Unsicherheit gilt: weniger, größer, ruhiger. Konkret vermeiden:

- Kacheln, Karten, Boxen mit Rahmen, Icon-Reihen, kleinteilige Teaser
- ein zweiter Flächenton, Gradienten, Bildfilter, Overlays
- Pill-Buttons (Ausnahme: der Newsletter-Button), Schatten, Glow
- animierte Effekte, die auf sich zeigen — die Bewegung soll den Scroll begleiten, nicht ihn kommentieren
- Umformulieren der Texte: alle Copy ist abgestimmt
