---
description: Registra treino de jiu-jitsu e marca Jiu-Jitsu no Diário
---

`$ARGUMENTS`: `fui no jiu, 5 rounds` · `aula completa 90min, passagem e meia-guarda, 2 finalizações a favor 1 sofrida`.

1. Data alvo (padrão hoje). Garanta a página do dia.
2. Crie em `🥋 Jiu-Jitsu` (`jiujitsu.data_source_id`):
   - `Nome` = `<Tipo> DD/MM` · `Data` · `Tipo` · `Duração (min)` · `Rounds` · `Finalizações a favor` · `Finalizações sofridas`
   - `Posições treinadas` (multi-select) a partir do que eu citei
   - `Faixa`: repita a última faixa registrada no banco. Se não houver nenhuma, deixe vazio e pergunte **uma vez**.
   - `Notas do treino` · `A corrigir` (o que eu disse que errei)
   - `Diário` = relation para o dia
3. Marque `Jiu-Jitsu` = true e recalcule `Score (%)`.
4. Uma linha: `✅ Jiu-Jitsu (Aula completa · 5 rounds · 2/1) · Jiu-Jitsu marcado · Score 55% → 64%`
