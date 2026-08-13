---
description: Lança uma saída no 💰 Financeiro
---

`$ARGUMENTS`: `42,90 gasolina pix` · `paguei 620 de insumos da cantina no boleto` · `almoço 28 débito`.

1. Data alvo (padrão hoje). Garanta a página do dia (para a relation).
2. Crie em `💰 Financeiro` (`financeiro.data_source_id`) com `Tipo` = **Saída**:
   - `Descrição` (o que eu falei, capitalizado) · `Data` · `Valor` (número; `42,90` → `42.90`)
   - `Mês` = `YYYY-MM` · `Pago` = true (salvo se eu disser "a pagar"/"vence dia X")
   - `Diário` = relation para o dia

3. **Inferência de Categoria / Centro:**

| Sinais | Categoria | Centro |
|---|---|---|
| gasolina, combustível, posto, álcool | Combustível | Pessoal |
| consórcio, moto, cb 300, twister | Moto/Consórcio | Pessoal (+ `Recorrente` ✓) |
| almoço, lanche, ifood, restaurante | Alimentação | Pessoal |
| mercado, supermercado, feira | Mercado | Pessoal |
| insumo, fornecedor, cantina | Cantina – Insumos | Cantina |
| api, openai, claude, servidor, domínio, saas | Software/SaaS | Nexar |
| academia, mensalidade academia | Academia | Pessoal |
| jiu, kimono, mensalidade jj | Jiu-Jitsu | Pessoal |
| faculdade, curso, livro técnico | Educação | Pessoal |
| farmácia, médico, exame | Saúde | Pessoal |
| revisão, óleo, pneu, oficina | Manutenção | Pessoal |
| resto | Outros | Pessoal |

`Método`: pix / débito / crédito / dinheiro / boleto. **Padrão: Pix.**

4. Declare a suposição em meia linha quando inferir Centro ou Método.
5. **Consórcio sem valor**: pergunte o valor. É a única pergunta permitida aqui.
6. Uma linha: `💸 Saída R$ 42,90 · Combustível · Pessoal · Pix · saldo do dia −R$ 42,90`
