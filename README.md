# Porto Velho (city): law history in git

Part of [lexifina/global-law](https://github.com/lexifina/global-law), one git history for every country's law: this is the law of Porto Velho, Rondônia, Brazil, which global-law reads at `brazil/rondonia/porto-velho/acts/`.

The municipal law of the Município de Porto Velho, the city of Porto Velho (Rondônia) (Brazil) as a git history: one file per Artigo, one paragraph per line, so `git blame`, `git log` and `git diff` work line by line. The text is Portuguese, the only official language.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law).

## What this repository holds

| Folder | Act | Versions |
| --- | --- | ---: |
| `lei-organica/` | Lei Orgânica do Município de Porto Velho (1990) and every amendment the Câmara's SAPL records | one per period of vigência (88) |

**Lei Orgânica only, with its history.** The Câmara's SAPL keeps the Lei Orgânica as a structured text with a view of the text in force for each period between amendments, so each amendment is a commit on the day its period starts, credited to the Emenda à Lei Orgânica that gave it. Ordinary and complementary laws are not in yet. State law is in [brazil-rondonia-law](https://github.com/lexifina/brazil-rondonia-law); federal law in [brazil-law](https://github.com/lexifina/brazil-law).

## Source

[Câmara Municipal de Porto Velho, SAPL](https://sapl.portovelho.ro.leg.br/norma/13615), published by the Câmara Municipal de Porto Velho. Each version names the page it was taken from and that page's sha256, in `data/versions.json`.

## Dates

The first version is the Lei Orgânica of 27 March 1990 as SAPL gives it in force from that day. Each later version is dated by the first day of the period of vigência SAPL gives it and credited to the act SAPL names for it ("Dada por Emenda à Lei Orgânica nº ..."). Two amendments of the same day are two versions of that day, in SAPL's order; a period SAPL ends before it starts is skipped. Commits are at noon in Porto Velho.

## How it is built

Lexifina reads the sources listed here and records each act's dated versions, and the laws that made each change, in one corpus file. `tools/build.py` writes this repository from that file, and the same corpus always gives the same commit hashes; `REPRODUCE.md` gives the details and the checks. A model (Claude) wrote Lexifina's code; it wrote no legal text, and no model runs when the history is built.

Each SAPL view becomes one file per Art.; each provision is one line, its label ("Art. 1º.", "§ 1º", "XV –") followed by its text; headings stand above the first article under them; `000-titulo.md` holds the preamble. The notes SAPL keeps under a provision or links into it ("Inclusão feita pelo ..."), provisions it marks as superseded and the amending acts' own blocks it shows inside the text are left out. Table rows are one line each, cells separated by ` | `.

## How it is checked

Every version is read back from git on the day it took effect (`tools/check_repo.py`) and must match the corpus; an independent letters-and-digits comparison of every version against the source page must show no difference. Results are in `REPRODUCE.md`.

## What "author" means

The author of each commit is the law that made the text, or, for a consolidated text, the publisher, with an e-mail address that cannot exist; the committer is always Lexifina.

## Limits

The history is SAPL's: a version is only as exact as the Câmara's structured text for that period. The text is not the official version: only the Diário Oficial do Município is authoritative.

## Licence

See [LICENSE](LICENSE): Brazilian law texts are not protected by copyright (Lei 9.610/1998, art. 8, IV). Fonte: Câmara Municipal de Porto Velho, SAPL, Câmara Municipal de Porto Velho.
