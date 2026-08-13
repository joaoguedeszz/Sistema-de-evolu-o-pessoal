---
description: Marca uma ou mais atividades do dia (linguagem solta)
---

`$ARGUMENTS` vem solto: `/feito treino, água 500ml, inglês` · `/feito bíblia e livro` · `/feito ontem: cardio`.

1. Detecte a data (padrão: hoje em America/Maceio; aceite `ontem`, `sexta`, `dia 8`). Garanta a página do dia como em `/dia`.
2. Mapeie cada item para a propriedade do `📅 Diário`:

| Termos | Checkbox |
|---|---|
| treino, academia, musculação, push, pull, legs | `Treino` |
| cardio, corri, corrida, esteira, bike | `Cardio` |
| abs, abdômen, core | `ABS` |
| jj, jiu, jiu-jitsu, luta, tatame | `Jiu-Jitsu` |
| bíblia, devocional | `Bíblia` |
| dev, java, spring, código, programei, ads, faculdade | `Dev` |
| ibge, concurso, estudei ibge | `Estudo IBGE` |
| inglês, english | `Inglês` |
| livro, leitura, li | `Livro` |
| pele, skincare | `Pele` |
| refeições, comi certo, dieta | `Refeições` |

3. `água` / `ml` / `L` → some em `Água (L)` (acumulativo: leia, some, escreva). `peso` → `Peso (kg)`. `sono`/`dormi` → `Sono (h)`. `energia` → select `Energia`.
4. Termo que não bate em nada: diga em meia linha o que ignorou. Não interrogue.
5. Recalcule `Score (%)` = concluídos ÷ 11 × 100 (10 checkboxes + meta de água batida) e escreva no dia.
6. Confirme em **uma linha**: `✅ Treino · Inglês marcados · Água 2,0/3,5 L · Score 45% → 64%`
