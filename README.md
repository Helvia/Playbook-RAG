# Playbook-RAG

Data released with the Playbook-RAG system demonstration (under review, EACL 2027, System Demonstrations). The evaluation test set and the anonymized source documents it was written from.

## Contents

- `data/documents/`: the nine source documents of the knowledge base: an HR handbook on external workers (contingent workers and contractors), anonymized. The knowledge base the paper evaluates on is these documents cut into 54 articles.
- `data/dataset.csv`: the 122 evaluation queries with their gold labels, one row per query. The queries were written from the documents, never from the knowledge map's detection signals, and every row was reviewed and edited by the authors against the documents.
- `data/map.json`: the knowledge map built from the documents and the article-level corpus with the `/helvia-kmap` knowledge map skill.

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

The article-level corpus, the system prompts and the per-run model outputs are part of the evaluation harness and are not released here.

## Citation

The paper is under review at EACL 2027 (System Demonstrations), so there is no proceedings reference or DOI yet. Until there is, cite it as unpublished work:

> Davide Aversa, Lefteris Loukas, Stratos Papadoudis and Stavros Vassos. *Ask, Don't Guess: A Human-Readable Playbook-RAG Method for Enterprise Knowledge Bases*. Under review at EACL 2027, System Demonstrations, 2026.

```bibtex
@misc{aversa2026playbookrag,
  title  = {{Ask, Don't Guess: A Human-Readable Playbook-RAG Method for Enterprise Knowledge Bases}},
  author = {Aversa, Davide and Loukas, Lefteris and Papadoudis, Stratos and Vassos, Stavros},
  year   = {2026},
  note   = {Under review at EACL 2027, System Demonstrations},
  url    = {https://github.com/Helvia/Playbook-RAG},
}
```

This entry is replaced with the proceedings reference once the paper appears.

## License

Copyright © 2026 Helvia Technologies PCC.

The documents, the dataset and the knowledge map are released under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license; see `LICENSE` for the full text. When you use them, attribute them as described under [Citation](#citation).
