---
description: Lança uma entrada no 💰 Financeiro
---

`$ARGUMENTS`: `entrou 380 na cantina hoje` · `recebi 1500 do cliente da Nexar` · `380 cantina`.

1. Data alvo (padrão hoje). Garanta a página do dia.
2. Crie em `💰 Financeiro` com `Tipo` = **Entrada**, `Pago` = true, `Mês` = `YYYY-MM`, `Diário` = relation.

| Sinais | Categoria | Centro |
|---|---|---|
| cantina, escola, vendas do dia, caixa | Cantina – Receita | Cantina |
| nexar, cliente, projeto, automação, mensalidade de cliente | Nexar – Receita | Nexar |
| salário, freela avulso, presente, reembolso | Outros | Pessoal |

`Método` padrão: **Pix**.

3. Sem centro explícito, assuma **Cantina** (renda base) e declare a suposição em meia linha.
4. Uma linha: `💰 Entrada R$ 380,00 · Cantina – Receita · Cantina · Pix · saldo do dia +R$ 317,10`
