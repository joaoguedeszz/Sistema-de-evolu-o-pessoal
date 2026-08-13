---
description: Fechamento mensal — dinheiro por categoria e por centro + evolução física
---

`$ARGUMENTS` opcional: `2026-07`. Padrão: mês corrente em America/Maceio.

1. Defina `Início` = dia 1 e `Fim` = último dia do mês.
2. `💰 Financeiro` — `WHERE "Mês" = 'YYYY-MM'`. Agrupe por `Categoria` e por `Centro`; separe Entradas e Saídas.
3. `📅 Diário` do período — dias com cada checkbox, média de água, peso início vs. fim, sono médio, score médio.
4. `🏋️ Musculação` / `🏃 Cardio` / `🥋 Jiu-Jitsu` — nº de sessões e volume/distância totais.
5. `📚 Estudos` — horas por trilha.
6. Compare com o mês anterior. Sem mês anterior, escreva `—`.

## Saída

```
🗓️  FECHAMENTO — AGOSTO/2026                Score médio: 61%

DINHEIRO
  Entradas   R$ 8.420,00     Saídas  R$ 6.980,00     Saldo  R$ 1.440,00
  (julho: saldo R$ 980,00 · +R$ 460,00)

  POR CENTRO           Entradas      Saídas       Saldo
    Cantina           R$ 7.200,00   R$ 4.100,00   R$ 3.100,00
    Nexar             R$ 1.220,00   R$   380,00   R$   840,00
    Pessoal           R$     0,00   R$ 2.500,00  −R$ 2.500,00

  TOP 5 SAÍDAS
    Cantina – Insumos   R$ 2.480,00
    Moto/Consórcio      R$   960,00
    ...

CORPO
  Peso 79,8 → 78,1 kg  (−1,7)      Sono médio 6,4 h
  Musculação 16x · Cardio 9x · Jiu-Jitsu 5x
  Água média 3,0 L/dia  (meta 3,5)

MENTE
  Java/Spring 34h · IBGE 11h · Inglês 18 dias · Leitura 12 dias

📌 Foco setembro: <uma frase, baseada no maior gap>
```

7. Grave em `📝 Relatórios`: `Tipo` = `Mensal`, `Período` = `YYYY-MM`, bloco no corpo.
8. Atualize `🎯 Metas` de horizonte Mensal/Trimestral/Anual: `Atual` e `Progresso (%)` = `Atual ÷ Alvo × 100`.
