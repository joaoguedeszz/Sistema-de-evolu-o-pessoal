---
description: Soma água ao dia (acumulativo)
---

`$ARGUMENTS`: `500ml` · `1L` · `1,5` · `dois copos` · `mais 300ml` · `ontem 2L`.

Conversões: `ml` ÷ 1000 · `L`/número solto = litros · **copo = 250 ml (0,25 L)** · `garrafa` = 500 ml salvo indicação contrária.

1. Data alvo (padrão hoje, America/Maceio). Garanta a página do dia.
2. **Leia `Água (L)` atual**, some o valor novo, **escreva o total**. Nunca sobrescreva com o incremento.
3. Se `$ARGUMENTS` for vazio, apenas relate o valor atual e o que falta para 3,5 L.
4. Se o total cruzou 3,5 L agora, recalcule `Score (%)` (a meta de água conta como 1 dos 11 itens).
5. Uma linha: `💧 +0,5 L · Água 2,5 / 3,5 L (falta 1,0 L)`
