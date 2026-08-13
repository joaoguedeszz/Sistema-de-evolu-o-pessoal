# SETUP — 6 passos, ~10 minutos

## 1. Criar a pasta e jogar os arquivos dentro

```bash
mkdir -p ~/sistema-joao && cd ~/sistema-joao
```
Coloque `PROMPT-CLAUDE-CODE.md`, `CLAUDE.md` e este `SETUP.md` aí dentro.

## 2. Conectar o MCP do Notion no Claude Code

O MCP que você conectou está no app do Claude — o Claude Code é separado e precisa do seu próprio registro.

```bash
claude mcp add --transport http notion https://mcp.notion.com/mcp --scope user
```

`--scope user` = vale em todas as pastas. Sem ele, só nesta.

Depois:
```bash
claude
```
E dentro do Claude Code:
```
/mcp
```
Autentique no navegador. Se o redirect falhar, cole a URL completa de callback no prompt que aparecer.

Confirme:
```bash
claude mcp list
```
Deve aparecer `notion` com status conectado.

## 3. Dar permissão de escrita no Notion

Na autenticação, o Notion pergunta a quais páginas dar acesso. **Marque o workspace inteiro** (ou no mínimo a página onde a Central de Comando vai morar). Sem isso, os `create` falham com erro de permissão.

## 4. Rodar o build

Dentro da pasta, abra o Claude Code e cole todo o conteúdo de `PROMPT-CLAUDE-CODE.md` (a partir da linha de corte). Ele vai:
- criar a Central de Comando + 9 bancos
- criar `notion-ids.json`, os slash commands e `LIMITACOES.md`
- popular metas, criar o dia de hoje e a semana atual
- rodar um teste de ponta a ponta

Deixe rodar. São muitas chamadas. Se pedir permissão de ferramenta, aprove.

## 5. Uso diário

```
cd ~/sistema-joao && claude
```
Depois é só falar:
```
> feito treino, bebi 1L, gastei 42,90 de gasolina no pix
> /status
> /relatorio
> /semana
```

## 6. Voz de verdade (o "Jarvis" falado)

Claude Code é terminal — não escuta voz. Duas opções reais:

**A) App do Claude no celular (recomendado para voz)**
O conector do Notion que você já ligou funciona lá. Use o ditado do teclado e fale: *"marca treino como feito e adiciona 1 litro de água"*. Para ele agir igual, crie um **Project** no app do Claude e cole o conteúdo do `CLAUDE.md` nas instruções do projeto. Mesmo sistema, mesma base, sem terminal.

**B) Ditado do sistema no terminal**
No Android/iOS via Termux não vale a pena. No desktop, use o ditado nativo do SO (Win+H no Windows, ditado do macOS) e fale direto no prompt do Claude Code.

---

## Manutenção

- **Semanalmente:** rode `/semana` no domingo à noite. É o que transforma registro em evolução.
- **Mensalmente:** `/mes` — o fechamento financeiro por centro (Pessoal/Cantina/Nexar) é o mais valioso pra você.
- Se um banco sumir ou o ID mudar, apague `notion-ids.json` e peça: *"reconstrua o cache de IDs"*.
