# How this repository was made (Porto Velho)

This file is written by the build on 2026-11-04, the day the source data was retrieved.

## Sources

| Source | Address | Retrieved | Licence |
| --- | --- | --- | --- |
| Câmara Municipal de Porto Velho, SAPL: Texto Articulado of the Lei Orgânica, one view per period of vigência | <https://sapl.portovelho.ro.leg.br/norma/13615> | 2026-11-04 | Text: Câmara Municipal de Porto Velho, SAPL (Sistema de Apoio ao Processo Legislativo), Lei Orgânica do Município de Porto Velho, sapl.portovelho.ro.leg.br. Lei 9.610/1998 art. 8 IV: the texts of laws and other official acts are not protected by copyright. Non-official text: only the Diário Oficial do Município is authoritative. |

Every word of law in this repository comes from these sources. Lexifina reads them and records each act's dated versions, and the laws that made each change, in one corpus file. This repository is built from that file.

## What is in it

| Act | Title | Versions | Span |
| --- | --- | ---: | --- |
| `lei-organica` | Lei Orgânica do Município de Porto Velho | 88 | 1990-03-27 to 2025-11-14 |

The build made 76 commits:

| Commits | Kind |
| ---: | --- |
| 1 | first version of an act |
| 75 | one law on its in-force day |
| 0 | changes no amendment note explains, credited to the publisher |

Other counts:
- 0 commits on the branch `futuro`: laws not yet in force on 2026-11-04.
- 0 commits dated 1 January 1970: in force before 1970, with the real day in their `In-force` trailer.
- 87 laws in the record.
- 152 tags.

## Dates

Each commit is dated at noon (America/Porto_Velho) on the day the change took effect. The other dates, enacted and published, are trailers.

When a law gives no date of its own, the default rule applies: The Lei Orgânica and its amendments are promulgated by the Mesa da Câmara and take effect as they state; this record dates each version by the first day of vigência SAPL gives it. https://sapl.portovelho.ro.leg.br/norma/13615

## How the history is built

`tools/build.py` turns the corpus into this history in one pass: one commit per law, on the day it took effect. The same corpus always gives the same commit hashes. `tools/check_repo.py` reads every version back from git and compares it with the corpus. `tools/on.py` shows the law as it stood on any date. The corpus format is described in `tools/SCHEMA.md`.

- Corpus: sha256 `c910e1b9b812a259ca5de4c8a8386e0093edf5dde4fb041eaa9c7b5c98119206` (398691 bytes).
- Builder blob hashes (`git hash-object`): `build.py` `35388bee5aa05369f7da68f5a8fa015ea8d442b8`, `check.py` `5d719354ea4c62d240c93d2cae446307d81d9e81`, `on.py` `aff48cf1b68d50c7ba8f399ca32261871c301824`.
- Python 3.14.4; git version 2.53.0.

## Checks

Not yet run for this build.

No second build of this corpus has been compared yet.

## Decisions made by hand

- Each version is one SAPL "vigência" view of the Lei Orgânica's Texto Articulado: the text in force from the view's first day, dated by that day and credited to the act SAPL says gave it ("Dada por ..."); the first view (from 27 March 1990) is credited to the Lei Orgânica itself. Where two views start on the same day (two amendments of the same date), both are kept, in SAPL order, as two versions of that day. Each unit that differs from the view before is credited to the act that gave the view.
- When the text SAPL shows as in force now (the norma page, with its "Vigência a partir de" day and "Dada por" act) starts after the last view, it is the last version. Where SAPL starts a period without naming an amending act, the units that changed are left uncredited and committed as publisher commits, not guessed.
- Each provision is one line: its label ("Art. 1º.", "§ 1º", "XV –") followed by its text; table rows are one line each, cells separated by " | ". Notes SAPL keeps under a provision or links into it ("Inclusão feita pelo ..."), provisions it marks as superseded and the amending acts own blocks it shows inside the text are left out.
- One file per Art.; headings stand above the first article under them; the "Ato das Disposições Orgânicas Transitórias", numbered from 1 again, is adt-*. "000-titulo" holds the preamble.

## What AI did and did not do

The scripts that read the sources and build this repository were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- Claude Code (claude-opus-5-5) wrote Lexifina's code and chose the sources. No model output is used as legal text or dates: every word comes from the SAPL pages.
