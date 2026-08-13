---
description: Registra cardio, calcula pace e marca Cardio no Diário
---

`$ARGUMENTS`: `corri 5km em 28min` · `esteira 20min 2,4km` · `bike 40min` · `hiit 15min forte`.

1. Data alvo (padrão hoje). Garanta a página do dia.
2. Crie em `🏃 Cardio` (`cardio.data_source_id`):
   - `Nome` = `<Modalidade> DD/MM` · `Data` · `Modalidade` · `Duração (min)` · `Distância (km)` · `FC média` · `Calorias` · `Percepção` · `Notas`
   - **`Pace (min/km)`**: só calcule se houver distância E duração. `pace = duração ÷ distância`, formatado `m:ss` (5 km em 28 min → `5:36`). Sem distância, deixe vazio.
   - `Diário` = relation para o dia
3. Marque `Cardio` = true e recalcule `Score (%)`.
4. Uma linha: `✅ Cardio (Corrida 5,0 km · 28min · 5:36/km) · Cardio marcado · Score 55% → 64%`
