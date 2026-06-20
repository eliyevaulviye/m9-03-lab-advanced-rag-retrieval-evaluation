# Eval Results — Lab 3 (Hybrid Search vs. Baseline)

## Eval set
5 questions over `knowledge_base.json`, each with an expected passage id. One question
(`0x80070005` error code) targets the exact-term failure mode of pure dense retrieval.

## Comparison table

| Setup | Retrieval Hit Rate | Faithfulness |
|---|---|---|
| Baseline (dense only) | 100% | 80% |
| Upgraded (hybrid: dense + BM25, RRF) | 100% | 100% |
| Hybrid + query rewriting (stretch) | 100% | 100% |

## Conclusion

Hybrid search (dense + BM25, RRF) made no difference to retrieval hit rate, moving it from 100% to 100% (+0%). Both setups retrieved the correct passage for the exact-term question. Faithfulness moved from 80% to 100% (+20%), which is expected since faithfulness mostly tracks whether the right passage was in context in the first place — better retrieval gives the generator better material to be faithful to.
