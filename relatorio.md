---
description: Relatório do dia — score, feitos, faltas, água, dinheiro, streaks
---

`$ARGUMENTS` opcional: data (`ontem`, `dia 8`). Padrão: hoje em America/Maceio.

## Coleta (uma query por banco — o plano não permite query cruzando bancos)

1. Página do dia no `📅 Diário` (crie se faltar).
2. Sessões do dia: `🏋️ Musculação`, `🏃 Cardio`, `🥋 Jiu-Jitsu`, `📚 Estudos` — `WHERE "date:Data:start" = '<data>'`.
3. `💰 Financeiro` do dia — some Entradas e Saídas, liste as categorias.
4. **Streaks**: puxe os últimos ~30 dias do `📅 Diário` ordenados por Data desc e conte dias consecutivos para trás, por checkbox. Streak de água = dias com `Água (L)` ≥ 3,5.

## Cálculo do Score — 11 itens, divisor fixo

O banco tem 11 checkboxes, mas `Cardio` e `ABS` **contam como um único slot** (no template original eles se alternam entre os dias). Isso fecha os 11 itens da regra:

| # | Item | Conta como feito quando |
|---|---|---|
| 1 | Treino | `Treino` ✓ |
| 2 | Cardio/ABS | `Cardio` ✓ **ou** `ABS` ✓ |
| 3 | Jiu-Jitsu | `Jiu-Jitsu` ✓ |
| 4 | Bíblia | `Bíblia` ✓ |
| 5 | Dev | `Dev` ✓ |
| 6 | Estudo IBGE | `Estudo IBGE` ✓ |
| 7 | Inglês | `Inglês` ✓ |
| 8 | Livro | `Livro` ✓ |
| 9 | Pele | `Pele` ✓ |
| 10 | Refeições | `Refeições` ✓ |
| 11 | Água | `Água (L)` ≥ 3,5 |

`Score (%)` = feitos ÷ 11 × 100, arredondado ao inteiro. **Escreva no campo `Score (%)` do dia.**

## Saída (formato fixo)

```
📊 RELATÓRIO — quarta, 12/08/2026        Score: 64%

CORPO
  ✅ Treino — Push A · 58min · RPE 8
  ✅ Cardio — Esteira 20min · 2,4km
  ❌ Jiu-Jitsu
  💧 Água 2,5 / 3,5 L  (falta 1,0 L)
  ⚖️ Peso 78,4 kg   😴 Sono 6,0 h

MENTE
  ✅ Dev — Spring Security · 1h20
  ✅ Inglês · ❌ Livro · ✅ Bíblia · ❌ IBGE

DINHEIRO (hoje)
  Entradas  R$ 380,00 (Cantina)
  Saídas    R$  62,90 (Combustível, Alimentação)
  Saldo     R$ 317,10

STREAKS
  Bíblia 9d · Água 3d · Treino 2d · IBGE 0d (quebrou ontem)

⚠️  Falta: Jiu-Jitsu, Livro, IBGE, 1,0 L de água.
```

## Gravação

Crie a página em `📝 Relatórios` (`relatorios.data_source_id`): `Título` = `Relatório Diário — DD/MM/AAAA`, `Data`, `Tipo` = `Diário`, `Score (%)`, `Destaques`, `Alertas`, `Período` = a data. O bloco acima vai no **corpo** da página, em code block.

## Regras

- Dado não encontrado é dado não encontrado. **Nunca invente número.**
- Se algo estiver em queda há 3+ dias, diga em **uma linha**. Uma vez. Sem sermão.
