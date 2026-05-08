

SINGLE WELL PETROPHYSICS PIPELINE — QC + FEATURE ENGINEERING + PARQUET
===========================================================================

Objetivo
--------
Implementar um pipeline blindado para analisar UM ÚNICO POÇO a partir de um arquivo LAS,
indo do carregamento bruto até a exportação em Parquet.

Escopo implementado
-------------------
1. LOAD LAS
2. HEADER / METADATA QC
3. CURVE INVENTORY
4. DEPTH QC
5. UNIT QC
6. RAW DATA OVERVIEW
7. STANDARDIZATION
8. INVALID VALUES
9. NULL ANALYSIS
10. DUPLICATES
11. PHYSICAL RANGE QC
12. OUTLIER INVESTIGATION
13. GEOLOGICAL CONSISTENCY CHECK
14. FEATURE ENGINEERING
15. DEPTH ALIGNMENT / RESAMPLING
16. EXPORT TO PARQUET

Filosofia do pipeline
---------------------
Este pipeline NÃO remove tudo automaticamente.

Em petrofísica, um valor estranho pode ser:
- dado ruim;
- ferramenta mal calibrada;
- unidade errada;
- placeholder de missing value;
- zona lavada;
- washout;
- gás;
- fratura;
- litologia especial;
- transição geológica;
- comportamento físico real.

Portanto, o pipeline separa três ideias:
1. dado inválido evidente -> pode virar NaN;
2. dado suspeito -> recebe flag de QC;
3. dado fisicamente plausível -> permanece para interpretação.

A ideia é gerar um dataset confiável, rastreável e pronto para analytics, rock physics,
geomecânica e, futuramente, FEniCS.
