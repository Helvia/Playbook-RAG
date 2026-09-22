# Playbook-RAG

Data released with the Playbook-RAG system demonstration (EACL 2027, System Demonstrations):
the evaluation test set and the anonymized source documents it was written from.

## Contents

- `data/documents/` — the nine source documents of the knowledge base: an HR handbook on
  external workers (contingent workers and contractors), anonymized. The knowledge base the
  paper evaluates on is these documents cut into 54 articles.
- `data/dataset.csv` — the 122 evaluation queries with their gold labels, one row per query.
  The queries were written from the documents, never from the knowledge
  map's detection signals, and every row was reviewed and edited by the authors against the
  documents.

## Columns of `data/dataset.csv`

| Column | Meaning |
| --- | --- |
| `id` | stable identifier of the query |
| `case` | one of eight cases: `ambiguous`, `near-miss` (expect a question); `specific`, `spurious`, `partial-coverage` (expect an answer); `false-premise` (expect a correction); `out-of-scope`, `missing-coverage` (expect a decline) |
| `expected` | the gold action: `ask`, `answer`, `correct` or `decline` |
| `query` | the user's message, first person |
| `entity` | the distinction the query turns on (for `near-miss`, the ambiguous phrase); empty where none applies |
| `value` | the value of that distinction the query names or that the documents cover, where one applies |
| `alternatives` | for queries that expect a question, the documented alternatives a closed follow-up must name, separated by ` \| ` |

## Not included

The knowledge map built from the documents, the article-level corpus, the system prompts and
the per-run model outputs are part of the evaluation harness and are not released here.

## License

Copyright (c) 2026 Helvia.

The documents and the dataset are released under the
[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)
license; see `LICENSE` for the full text. Please cite the paper when you use them.
