---
description: Garante a página de hoje no 📅 Diário e mostra feito x falta
---

Argumento opcional (`$ARGUMENTS`): uma data ou expressão relativa (`ontem`, `sexta`, `dia 8`). Sem argumento = hoje.

1. Calcule a data alvo em **America/Maceio**. Derive `Dia da Semana` (Seg…Dom) e `Semana` ISO (`YYYY-Www`).
2. Leia `notion-ids.json`. Consulte `diario.data_source_id` com SQL:
   `SELECT * FROM "collection://<diario_ds>" WHERE "date:Data:start" = '<YYYY-MM-DD>'`
3. Se **existir**, use. Se **não existir**, crie com `Nome` = `YYYY-MM-DD (Dia)`, `Data`, `Dia da Semana`, `Semana`, `Cidade` = `União dos Palmares`, e relacione em `Semana (ref)` ao registro da semana em `📊 Semanas` (crie a semana se faltar, com Início=segunda e Fim=domingo).
   **Nunca crie uma segunda página para a mesma data.**
4. Responda no formato:

```
📅 2026-08-12 (Qua) · W33          Score 36%
✅ Treino · Bíblia · Dev · Refeições
❌ Cardio · ABS · Jiu-Jitsu · IBGE · Inglês · Livro · Pele
💧 1,5 / 3,5 L
```

Se a página acabou de ser criada, diga `(página criada agora)` no fim da primeira linha.
