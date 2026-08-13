---
description: Fecha a semana — atualiza 📊 Semanas e compara com a anterior
---

`$ARGUMENTS` opcional: `2026-W32` ou `semana passada`. Padrão: semana ISO atual.

## Passos

1. Determine a semana ISO (segunda→domingo, America/Maceio). Guarde `Início` e `Fim`.
2. Em `📊 Semanas` (`semanas.data_source_id`): busque `Semana = 'YYYY-Www'`. Crie se não existir. **Nunca duplique.**
3. Consulte o período (uma query por banco):
   - `📅 Diário` — `WHERE "date:Data:start" BETWEEN '<ini>' AND '<fim>'`. Relacione todos os dias em `Dias`.
   - `🏋️ Musculação`, `🏃 Cardio`, `🥋 Jiu-Jitsu` — contagem de sessões.
   - `📚 Estudos` — soma de `Tempo (min)`.
   - `💰 Financeiro` — soma de Entradas, Saídas, top 3 categorias de saída.
4. Escreva em `📊 Semanas`: `Entradas (R$)`, `Saídas (R$)`, `Saldo (R$)`, `Retrospectiva`, `Foco da próxima`, `Nota da semana` (1–5).
   Os rollups (`Água média`, `Dias de treino`, `Score médio`, `Peso médio`, `Sono médio`…) se preenchem sozinhos pela relation `Dias` — **não escreva neles**. Eu não consigo lê-los por SQL, então recalculo pelos dias para o texto (ver `LIMITACOES.md` item 3).
5. Busque a semana **anterior** no mesmo banco para os deltas. Se não existir, escreva `—` no lugar do delta. **Não invente.**

## Saída

```
📈 SEMANA 2026-W33  (10/08 – 16/08)          Nota: 3,8/5

FREQUÊNCIA          Real / Meta      vs. W32
  Musculação          4 / 4   ✅       =
  Cardio              2 / 3   ⚠️      -1
  Jiu-Jitsu           1 / 2   ⚠️      +1
  Água (média)      3,1 / 3,5 L ⚠️   +0,3
  Estudo             8h20 / 10h ⚠️   -1h10

CORPO
  Peso: 78,9 → 78,4 kg  (-0,5)
  Sono médio: 6,2 h  ⚠️ abaixo de 7h

DINHEIRO
  Entradas   R$ 2.140,00
  Saídas     R$ 1.680,00
  Saldo      R$   460,00   (W32: R$ 210,00)
  Top 3 saídas: Cantina–Insumos 620 · Moto/Consórcio 480 · Combustível 190

📌 Foco W34: fechar 3 cardios e subir sono para 7h.
```

Metas de referência (do `🎯 Metas`): Musculação 4x · Cardio 3x · JJ 2x · Água 3,5 L · Java/Spring 10h · Inglês 5x · Leitura 5x · Bíblia 7x.

6. Grave também em `📝 Relatórios`: `Tipo` = `Semanal`, `Período` = `YYYY-Www`, bloco no corpo.
7. **Sempre mostre delta.** Semana ruim é dita uma vez, com número, sem sermão.
