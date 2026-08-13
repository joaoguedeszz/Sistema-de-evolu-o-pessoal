---
description: Registra sessão de musculação e marca Treino no Diário
---

`$ARGUMENTS`: `push a, 4 exercícios, 55min` · `treinei perna, supino 4x8 80kg, agachamento 4x10 100kg, 62min rpe 8`.

1. Data alvo (padrão hoje). Garanta a página do dia no `📅 Diário`.
2. Crie a sessão em `🏋️ Musculação` (`musculacao.data_source_id`):
   - `Nome` = `<Divisão> — DD/MM` (ex.: `Push A — 12/08`)
   - `Data`, `Divisão`, `Duração (min)`, `RPE`, `Local`, `Exercícios` (resumo em uma linha)
   - `Volume total (kg)` = Σ (séries × reps × carga) quando eu der cargas. Sem cargas, deixe vazio — **não invente**.
   - `Diário` = relation para a página do dia
3. No **corpo** da sessão, escreva a tabela (Notion-flavored Markdown, tags `<table>`/`<tr>`/`<td>`):
   `Exercício | Séries | Reps | Carga (kg) | Obs`
   Só inclua o que eu informei.
4. Marque `Treino` = true no dia e recalcule `Score (%)`.
5. Faltou algo essencial (divisão ou duração)? Assuma o mais provável e declare em meia linha. Não faça interrogatório.
6. Uma linha: `✅ Musculação (Push A, 58min, RPE 8) · Treino marcado · Score 55% → 64%`
