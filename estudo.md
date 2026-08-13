---
description: Registra estudo e marca o checkbox da trilha
---

`$ARGUMENTS`: `45min Spring Security` · `1h de inglês no Duolingo` · `2h IBGE estatística` · `li 30min de Clean Code`.

1. Data alvo (padrão hoje). Garanta a página do dia.
2. Infira a **Trilha** e o checkbox correspondente:

| Trilha | Sinais | Checkbox no Diário |
|---|---|---|
| `Java/Spring` | java, spring, jpa, hibernate, api, backend | `Dev` |
| `ADS UNINASSAU` | faculdade, uninassau, ads, av1, prova | `Dev` |
| `IBGE` | ibge, concurso, estatística, raciocínio lógico | `Estudo IBGE` |
| `Inglês` | inglês, english, duolingo, listening | `Inglês` |
| `Leitura` | livro, li, capítulo, leitura | `Livro` |
| `Nexar/Negócios` | nexar, cliente, proposta, automação, negócio | *(nenhum)* |
| `Outros` | resto | *(nenhum)* |

3. Crie em `📚 Estudos` (`estudos.data_source_id`): `Nome` = `<Trilha> — <Assunto>` · `Data` · `Trilha` · `Assunto` · `Tempo (min)` · `Recurso` · `Entregável` · `Anotações` · `Diário` (relation).
   Converta `1h20` → 80 min.
4. Marque o checkbox da trilha e recalcule `Score (%)`.
5. Uma linha: `✅ Estudo (Java/Spring · Spring Security · 45min) · Dev marcado · Score 55% → 64%`
