# LIMITAÇÕES — o que a API do Notion não automatizou

Build de 2026-08-12. Tudo aqui precisa de ajuste manual na interface do Notion **ou** é compensado por cálculo do agente.

---

## 1. Filtros de data relativa não funcionam via API 🔴 (ajuste manual)

A DSL de views só aceita valores **exatos**. Ao pedir `Data is today`, a API gravou `{"type":"exact","value":"today"}` — a view voltou **vazia** no teste. Foi removido para não enganar.

**Views afetadas e o conserto (30 segundos cada, na UI):**

| Banco | View | Filtro a adicionar na mão |
|---|---|---|
| `📅 Diário` | **Hoje** | `Data` → `Is` → `Today` |
| `📅 Diário` | **Semana (Board)** | `Data` → `Is within` → `This week` |
| `💰 Financeiro` | **Este mês** | trocar o filtro `Mês is 2026-08` por `Data` → `Is within` → `This month` |

Enquanto não ajustar: `Hoje` está ordenada por Data desc (o dia de hoje fica na primeira linha) e `Este mês` filtra pelo campo de texto `Mês` — funciona, mas você precisa trocar `2026-08` todo mês.

**Isso não afeta a operação do agente.** Eu consulto por SQL com a data calculada, nunca dependo dessas views.

---

## 2. Fórmulas: não foram criadas 🟡 (o agente calcula)

Nenhuma propriedade `formula` foi criada. Os campos abaixo são `number` e **eu escrevo o valor**:

| Banco | Campo | Quem calcula |
|---|---|---|
| `📅 Diário` | `Score (%)` | agente, em `/relatorio` — concluídos ÷ 11 × 100 |
| `🏃 Cardio` | `Pace (min/km)` | agente (texto `mm:ss`, ex. `5:36`) — número não representa 5:36 direito |
| `📊 Semanas` | `Entradas (R$)`, `Saídas (R$)`, `Saldo (R$)` | agente, em `/semana` — rollup direto para o Financeiro não é possível (ver item 3) |
| `🎯 Metas` | `Progresso (%)` | agente — `Atual ÷ Alvo × 100` |
| `📚 Estudos` | `Progresso (%)` | você ou o agente, manual |

Se quiser fórmulas nativas, dá para criar na UI. Mas aí o agente para de escrever nesses campos — avise antes.

---

## 3. Rollups: criados, mas com duas ressalvas 🟡

**Criados com sucesso** em `📊 Semanas` (sobre a relation `Dias`):
`Água média (L)` · `Dias de treino` · `Dias de cardio` · `Dias de JJ` · `Score médio` · `Peso médio` · `Sono médio`

**Ressalva A — não são legíveis por SQL.** A API marcou os 7 como `notAvailableInQuerySql`. Eles aparecem certos na interface do Notion, mas eu **não consigo lê-los** via `query_data_sources`. Nos relatórios eu recalculo a partir das linhas do `📅 Diário`. Consequência prática: zero. Só não estranhe se eu nunca citar o rollup e sim o número recalculado.

**Ressalva B — rollup financeiro não existe.** `📊 Semanas` não tem relation para `💰 Financeiro` (o Financeiro se relaciona com o `📅 Diário`, não com a Semana). Entradas/Saídas/Saldo da semana são somados por query e escritos nos campos `number`.

---

## 4. Casas decimais dos números 🟢 (cosmético)

A API não expõe precisão decimal. `Água (L)`, `Peso (kg)`, `Sono (h)` e `Distância (km)` foram criados como número simples — o Notion mostra o que for gravado (`2.5`, `78.4`). Se quiser travar em 1 casa: abra a propriedade → *Number format* → escolha.

`Valor` (Financeiro) e os três campos `R$` de Semanas **saíram certos**, com formato **Real brasileiro**.

---

## 5. Relations: todas criadas ✅

Nada pendente. As 6 relations bidirecionais do `📅 Diário` (`Musculação`, `Cardio (sessões)`, `Jiu-Jitsu (sessões)`, `Estudos`, `Financeiro`, `Semana (ref)`) foram criadas no DDL de cada banco filho e verificadas por fetch.

---

## 6. Não consigo apagar páginas 🔴 (ajuste manual)

O MCP do Notion **não expõe nenhuma ferramenta de exclusão/arquivamento de página**. Testei `in_trash: true` no `update_page` — foi aceito sem erro e **não fez nada**; a linha continuou lá.

**Consequência:** quando você pedir para apagar um lançamento, eu vou **zerar o valor, limpar as relations e renomear** para `🗑️ ... — PODE APAGAR`. O registro para de afetar qualquer total, mas continua visível até você deletar na interface (botão direito na linha → *Delete*).

**Pendente agora:** uma linha em `💰 Financeiro` chamada `🗑️ TESTE DO BUILD — PODE APAGAR` (R$ 0,00). Sobrou do teste de ponta a ponta. Apague quando abrir o banco.

---

## 7. Limite de plano 🟢 (informativo)

O workspace está em plano sem Notion AI Business. Efeito: `query_data_sources` tem **cota compartilhada** de uso e query cruzando dois bancos ao mesmo tempo **não é permitida** (exige Enterprise). Por isso os relatórios fazem uma query por banco e eu cruzo os dados aqui. Nenhuma perda de função.
