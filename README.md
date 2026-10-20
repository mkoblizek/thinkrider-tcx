# ThinkRider → TCX

Převodník rozpracovaných záznamů jízd (`.tmp`) z aplikace **ThinkRider** pro Windows na soubory **TCX**, které přijme Strava, Garmin Connect nebo intervals.icu.

Hodí se, když aplikace hlásí, že se cvičení nepodařilo uložit, a jízda se neobjeví v historii. Záznam po vteřinách často zůstane na disku jako `.tmp` soubor a dá se z něj obnovit.

**Spuštění:** stačí otevřít `index.html` v prohlížeči, nebo použít verzi na GitHub Pages. Vše běží lokálně v prohlížeči, žádná data se nikam neodesílají.

## Použití

1. Najděte soubory `.tmp` ve složce `%USERPROFILE%\AppData\LocalLow\ZhiXingPai\ThinkRider` (cestu vložte do adresního řádku Průzkumníka).
2. Přetáhněte je na stránku nebo je vyberte klepnutím. Víc souborů téže jízdy (stejné RecordId) se sloučí, použije se ten nejdelší.
3. Stáhněte TCX: jednu jízdu přímo jako `.tcx`, víc jízd najednou jako ZIP.
4. Ve Stravě aktivitu po nahrání přepněte na virtuální jízdu a použijte „Opravit převýšení“, protože záznam neobsahuje nadmořskou výšku v bodech.

## Formát `.tmp`

První řádek je hlavička `#Klíč:hodnota;…` (mimo jiné `RecordId`, `RouteId`, `StartTime` v UTC). Další řádky mají 12 hodnot oddělených čárkou:

| # | Význam |
|---|--------|
| 1 | čas od startu (s) |
| 2 | výkon (W) |
| 3 | rychlost (km/h) |
| 4 | ujetá vzdálenost (km) |
| 5 | kadence (rpm) |
| 6 | tep (bpm) |
| 7, 8 | zeměpisná šířka, délka |
| 9 | nepoužito (0) |
| 10 | energie (kJ, kumulativně; ÷ 4,184 = kcal) |
| 11 | nastoupáno (m, kumulativně) |
| 12 | nepoužito (0) |

Význam sloupců je odvozený z naměřených dat, ne z oficiální dokumentace. Ověřeno na verzi ThinkRider 3.0.7.

## GitHub Pages

Settings → Pages → Source: *Deploy from a branch*, větev `main`, složka `/ (root)`. Stránka pak poběží na `https://<uživatel>.github.io/<repozitář>/`.

## Licence

MIT, viz [LICENSE](LICENSE). Projekt nesouvisí s výrobcem aplikace ThinkRider.
